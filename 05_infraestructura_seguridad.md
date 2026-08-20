# 05 · Análisis de infraestructura y seguridad — iteshu.edu.mx

> Reconocimiento técnico no intrusivo realizado el **20 de agosto de 2026** con
> herramientas estándar (`dig`, `curl -I`, `openssl s_client`, `whois`).
> Solo se consultaron cabeceras HTTP, registros DNS públicos y certificados TLS.
> No se realizaron escaneos de puertos, pruebas de intrusión ni carga.

---

## 1. Mapa de infraestructura (plataformas e IPs)

| Plataforma | Host / IP | Servidor detectado | Estado |
|---|---|---|---|
| Sitio institucional | `iteshu.edu.mx` / `www` → **200.79.181.209** | nginx + PHP 8.3.33 + PleskLin | ✅ Moderno; HTTP→HTTPS forzado (301) |
| Moodle ("Mi Escuela en Casa") | `cursos.iteshu.edu.mx` → **200.79.181.209** | nginx + PHP 8.3.33 | ✅ Con `X-Frame-Options: sameorigin` |
| Portal de fichas / admisión | `fichas.iteshu.edu.mx` → **200.79.178.211** | Apache 2.4.6 · OpenSSL 1.0.2k-fips · PHP 7.1.24 (CentOS 7) | 🔴 Stack EOL; certificado autofirmado vencido |
| Portal Alumno (control escolar) | `200.79.178.210/huichapanalu/` | Microsoft-IIS/8.5 (Windows Server 2012 R2) + ASP clásico | 🔴 Solo HTTP, sin TLS |
| DNS autoritativo | `ns1` / `ns2.iteshu.edu.mx` | Autoalojado en el mismo dominio | 🟠 Punto único de falla |
| Correo | Google Workspace | SPF (`~all`) + DMARC (`p=quarantine`) | ✅ Bien configurado |

Todo el ecosistema web vive en **3 IPs públicas propias** del bloque
`200.79.178.x – 200.79.181.x` (MX), sin CDN ni WAF delante.

---

## 2. Hallazgos críticos de seguridad

### H1 · Certificado autofirmado vencido en el portal de admisión 🔴
- `fichas.iteshu.edu.mx` presenta un certificado **autofirmado**
  (`CN=peji.iteshu.edu.mx`, emisor = sujeto, campos "SomeState/SomeCity")
  **vencido el 15 de enero de 2020** — más de 6 años.
- Impacto: todo aspirante que registra su ficha o paga en línea ve la pantalla
  roja de "su conexión no es privada". Se entrena a los usuarios a aceptar
  alertas de seguridad (hábito peligroso) y se pierde confianza justo en el
  paso que genera ingresos.
- Dato clave: **el instituto ya contrata un comodín GoDaddy `*.iteshu.edu.mx`**
  (vigente hasta feb 2027, instalado en www/cursos). Instalarlo también en
  `fichas` cuesta **$0 y se hace en minutos**.

### H2 · Software de servidor fuera de soporte (EOL) 🔴
| Componente | Versión detectada | Fin de soporte |
|---|---|---|
| PHP en `fichas` | 7.1.24 | dic 2019 (sin parches desde entonces) |
| Apache en `fichas` | 2.4.6 (CentOS 7) | CentOS 7 EOL: jun 2024 |
| OpenSSL en `fichas` | 1.0.2k-fips | EOL 2019 |
| Windows/IIS Portal Alumno | IIS 8.5 = Windows Server 2012 R2 | oct 2023 |

- El sistema que captura datos personales y pagos de aspirantes corre sobre
  versiones sin parches de seguridad desde hace años.

### H3 · Credenciales de alumnos viajan sin cifrar 🔴
- El Portal Alumno (`200.79.178.210/huichapanalu/`) **no tiene HTTPS**: el
  login de control escolar (calificaciones, horarios, datos personales) viaja
  en texto claro por la red (HTTP 200, cookie `ASPSESSIONID` sin flags).
- Además no redirige a HTTPS porque directamente no escucha con TLS.

### H4 · Sin cabeceras de seguridad ni cookies endurecidas 🟠
- En `www.iteshu.edu.mx` **no hay** `Strict-Transport-Security` (HSTS),
  `Content-Security-Policy`, `X-Frame-Options`, `X-Content-Type-Options` ni
  `Referrer-Policy`.
- La cookie de sesión se emite como
  `PHPSESSID=…; path=/` — **sin `Secure`, `HttpOnly` ni `SameSite`**.

### H5 · Divulgación de versiones 🟠
- Cabeceras exponen tecnología exacta: `server: nginx`,
  `x-powered-by: PHP/8.3.33`, `PleskLin`, `Apache/2.4.6`, `PHP/7.1.24`,
  `Microsoft-IIS/8.5`. Facilita el trabajo de reconocimiento a un atacante.

### H6 · DNS autoalojado sin respaldo externo 🟠
- `ns1`/`ns2` son hijos del propio dominio. Si el enlace o el servidor de DNS
  cae, caen el sitio, el correo y las fichas a la vez. No hay proveedor
  secundario externo visible.

### H7 · Ausencia de registro CAA 🟡
- No existe registro CAA que restrinja qué CA puede emitir certificados para
  el dominio (endurecimiento barato contra emisión fraudulenta).

### Puntos positivos ✅
- Servidor principal moderno (nginx + PHP 8.3 + Plesk) con redirect HTTPS.
- DMARC estricto (`p=quarantine`, `adkim=s; aspf=s`) + SPF correctos.
- Moodle con `X-Frame-Options`; TLS 1.2/1.3 disponible incluso en `fichas`.
- Certificado comodín vigente ya contratado (reutilizable en todos los hosts).

---

## 3. Plan de mejora priorizado

| # | Acción | Esfuerzo | Impacto | Plazo |
|---|---|---|---|---|
| 1 | Instalar el comodín GoDaddy `*.iteshu.edu.mx` en `fichas` y forzar HTTPS | Muy bajo (horas) | Elimina alertas del navegador en admisiones | Inmediato |
| 2 | Poner el Portal Alumno detrás de TLS (proxy nginx en 200.79.181.209 o certificado en IIS) | Bajo | Cifra credenciales de alumnos | 1 semana |
| 3 | Añadir cabeceras de seguridad en nginx (HSTS, X-Content-Type-Options, Referrer-Policy, CSP básica, X-Frame-Options) y flags `Secure; HttpOnly; SameSite=Lax` en cookies | Bajo | Mitiga XSS/clickjacking/secuestro de sesión | 1 semana |
| 4 | Ocultar versiones: `server_tokens off`, `expose_php=Off`, quitar `X-Powered-By` | Muy bajo | Reduce superficie de reconocimiento | Inmediato |
| 5 | Migrar `fichas` de PHP 7.1/CentOS 7 al servidor Plesk (PHP 8.3) o actualizar a AlmaLinux/Rocky 9 | Medio | Elimina stack sin parches | 1–2 meses |
| 6 | Modernizar Portal Alumno (IIS 8.5/ASP clásico → plataforma soportada) | Alto | Elimina SO EOL | 3–6 meses |
| 7 | Alta de DNS secundario externo (proveedor gratuito o del registrador) | Bajo | Elimina punto único de falla | 1 semana |
| 8 | Publicar registro CAA (`0 issue "godaddy.com"`) | Muy bajo | Endurece emisión de certificados | Inmediato |
| 9 | Evaluar CDN/WAF (p. ej. Cloudflare gratuito) delante del sitio público | Bajo | Anti-DDoS, caché, TLS uniforme | 1 mes |

**Regla de oro:** ninguna acción requiere comprar software nuevo; los pasos
1, 2, 3, 4, 7 y 8 usan recursos que el instituto **ya tiene contratados**.

---

## 4. Metodología y evidencia (comandos)

```bash
dig +short A iteshu.edu.mx www fichas cursos        # → IPs del mapa
dig +short NS/MX/TXT/SOA iteshu.edu.mx              # → DNS, Google, SPF/DMARC
curl -sI https://www.iteshu.edu.mx/iteshu/          # → nginx, PHP 8.3, PleskLin, cookie sin flags
curl -sIk https://fichas.iteshu.edu.mx/             # → Apache 2.4.6, PHP 7.1.24, sin redirect
curl -sI http://200.79.178.210/huichapanalu/        # → IIS/8.5, solo HTTP
echo | openssl s_client -connect fichas...:443      # → autofirmado CN=peji, vencido 2020-01-15
echo | openssl s_client -connect www...:443         # → GoDaddy *.iteshu.edu.mx vigente
```

*Este documento complementa `03_diagnostico_web.md` (UX) con la capa de
infraestructura; ambos alimentan las diapositivas técnicas de `presentacion.html`.*
