# Matriz de políticas y accesos

La política existente no prueba por sí sola el comportamiento. La columna "Observado" solo se llena con evidencia.

| # | Origen | Destino | Servicio | Esperado | Observado | Control relacionado | Evidencia | Estado |
|---|---|---|---|---|---|---|---|---|
| 1 | Cliente remoto (VPN) | Jump | HTTPS, RDP | Permitido | TCP 443 y 3389 abiertos | BASICO-to-JUMP / PRIV-to-JUMP | TEST-01, TEST-02 | Aprobada |
| 2 | Cliente remoto (VPN) | Web | 443, 22, ICMP | Denegado | Fallan con origen 10.25.98.10; falta log de denegación | Ausencia de política + Implicit Deny | TEST-14, TEST-15 | Parcial |
| 3 | Jump | Web | HTTPS | Permitido | HTTP 200 | JUMP-to-WEB | TEST-05, TEST-07 | Aprobada |
| 4 | Jump | Web | RDP | Permitido | Login de xrdp del Web visible desde el Jump; inicio de sesión fallido | JUMP-to-WEB | TEST-09, TEST-17, TEST-18 | Parcial |
| 5 | Jump | Web | SSH | Permitido | Sesión SSH | JUMP-to-WEB | TEST-08 | Aprobada |
| 6 | Jump | Web | Otros (445) | Denegado | Sin respuesta; no concluyente | Implicit Deny (sin log) | TEST-11 | No concluyente |
| 7 | Usuario sin privilegios | Aplicaciones | RemoteApp | Solo Firefox | Un icono (usuario no visible) | RA-Normal | RDS-04, RDS-11/12 | Parcial |
| 8 | Usuario sin privilegios | Jump | SSH | Denegado | Deny: policy violation; TCP 22 falla | DENY-SSH-BASICO-JUMP | TEST-10, TEST-15, TEST-16 | Aprobada |
| 9 | Usuario sin privilegios | Web | SSH | Denegado | TCP 22 falla con origen 10.25.98.10; sin log de la política | DENY-SSH-BASICO-WEB | TEST-15 | Parcial |
| 10 | Usuario con privilegios | Aplicaciones | RemoteApp | Firefox, PuTTY, mstsc | Tres iconos (usuario no visible) | RA-Priv | RDS-06/07, RDS-09 | Parcial |
| 11 | Usuario sin privilegios | Jump | RDP directo | A definir | Sin prueba | BASICO-to-JUMP permite 3389 | — | **Pendiente** |
| 12 | Usuarios | Redes no autorizadas | Cualquiera | Denegado | Sin prueba | Implicit Deny | — | **Pendiente** |

**Diferencia entre controles.** La fila 7 y la 10 evalúan **RemoteApp**; las filas 1–6, 8, 9 evalúan **red**. Son independientes.
