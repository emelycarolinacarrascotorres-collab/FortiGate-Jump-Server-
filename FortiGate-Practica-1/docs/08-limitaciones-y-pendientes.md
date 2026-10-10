# 08 · Limitaciones, hallazgos y pendientes

## A. Pendientes de evidencia (impiden declarar cumplimiento)

| # | Pendiente | Impacto | Cómo cerrarlo (por GUI en el FortiGate) |
|---|---|---|---|
| P1 | VPN → Web denegado con origen real 10.25.98.10 | Requisito central | Ruta forzada por el adaptador del túnel; pruebas 443/22/ping; log en Forward Traffic |
| P2 | SSH de Emely al Web denegado | Requisito del perfil básico | Intento SSH a 10.25.97.114 con la VPN de Emely; log de DENY-SSH-BASICO-WEB |
| P3 | Sesión RDP Jump → Web | Requisito | Abrir mstsc desde RD Web con `usr_priv` y destino `10.25.97.114` |
| P4 | Sistema de Caja | Requisito | Publicar y capturar la página real, con `ls /var/www/html` |
| P5 | Vínculo `usr_priv`/`usr_normal` ↔ Alicia/Emely | Trazabilidad | Pestaña Cuenta de cada usuario en AD |
| P6 | Usuario visible junto a los iconos de RD Web | Perfiles | Panel Conexiones de COL-JUMP |
| P7 | Ping ISP/FortiGate/Cisco | Conectividad | `ping` desde ISP y desde CISCO-SRV |
| P8 | Fase 1/Fase 2 completos | Documentación | Pantalla de edición del túnel |
| P9 | Intento RDP directo del perfil básico al Jump | Control de red vs. RemoteApp | `mstsc` a 10.25.97.106 con Emely |
| P10 | Cliente web HTML5 (si se exige) | Requisito | Captura de `/RDWeb/webclient` |
| P11 | Enlace del video | Entrega | Ver [`video/README.md`](../video/README.md) |
| P12 | Registro de denegaciones implícitas | Auditoría | Activar *Log Violation Traffic* o añadir una política de denegación explícita con registro |

## B. Riesgos de seguridad observados

| Riesgo | Detalle | Recomendación |
|---|---|---|
| Cifrado de Fase 1 débil | DES-SHA256 | AES-256 |
| IKEv1 Aggressive + PSK | Exposición de la PSK a ataque offline | IKEv2 / certificados |
| Selectores 0.0.0.0/0 | Sin aislamiento a nivel de selector | Mantener la restricción en políticas |
| Administración en WAN | HTTP, HTTPS, SSH y FMG-Access en port1; HTTP en MGMT | Deshabilitar HTTP; limitar con *trusted hosts* |
| SVC-JUMP-TO-WEB incluye HTTP | Excede el requisito | Retirarlo |
| Sin 2FA | Usuarios locales sin segundo factor | Habilitar |
| Jump = controlador de dominio | Un servidor expuesto a usuarios remotos aloja AD/DNS | Separar roles |
| Sin inspección | Políticas con `no-inspection` | Aplicar perfiles de seguridad |
| ISP | Consola con privilegio 15 y `exec-timeout 0`; `line vty` con `login` sin contraseña | Endurecer |
| Cisco-SRV | `exec-timeout 5` en consola, SSH v2 | Adecuado; mantener |

## C. Inconsistencias detectadas

1. **Content-Length 40 vs. página por defecto de Apache** (ver T06).
2. **`weadmin` vs. `webadmin`** en el cuadro de mstsc.
3. **Dos identidades paralelas** (FortiGate vs. AD) sin vínculo técnico.
4. **Kernel `7.0.0-38-generic`** indicado en el banner de Ubuntu: no se cita como dato verificado. Verificar con `uname -r`.
5. **Hora de los equipos**: no se verificó que los relojes estén sincronizados; las capturas se tomaron en momentos distintos y no se deben correlacionar por hora sin comprobarlo.
6. **Nombre del archivo `Running-Config_R1`**: el hostname es `CISCO-SRV`.
7. **Windows 10 conectado al FortiGate** (topología): función no documentada.

## D. Material excluido
- Una captura ajena a la práctica (pregunta de examen sobre evidencia digital) **no** forma parte del repositorio.
- Capturas duplicadas (misma imagen con otro nombre) se conservan una sola vez; ver [`evidencias/INVENTARIO.md`](../evidencias/INVENTARIO.md).
