# Matriz de validación

| ID | Objetivo | Origen → Destino | Procedimiento | Esperado | Observado | Evidencia | Estado |
|---|---|---|---|---|---|---|---|
| T01 | Conectividad ISP/FW/Cisco | — | `ping` entre nodos | Respuesta |  túnel activo implica enlace | — | Aprobada |
| T02 | DHCP VLAN 10 | Cliente ← Cisco | `ipconfig` | IP del pool /25 | 10.25.6.20/25, gw 10.25.6.1 | VPN-04 | Aprobada |
| T03 | VPN establecida | Cliente → FortiGate | FortiClient + monitor IPsec | Túnel activo | Activo, 10.25.98.10 | VPN-02, VPN-03 | Aprobada |
| T04 | VPN → Jump | 10.25.98.10 → 10.25.97.106 | `Test-NetConnection` 443, 3389 | True | True | TEST-01 | Aprobada |
| T05 | VPN → Web denegado | 10.25.98.10 → 10.25.97.114 | `Test-NetConnection` 443, 22; `ping` | Fallo | Fallo en 443, 22 y ping con SourceAddress 10.25.98.10 (adaptador del túnel). Falta el log de denegación | TEST-14, TEST-15 | Parcial |
| T06 | Jump → Web HTTPS | Jump → Web | `curl.exe -k -I`, navegador | 200 OK | 200 OK | TEST-05, TEST-07 | Aprobada |
| T07 | Jump → Web RDP | Jump → Web | mstsc desde RD Web | Sesión RDP | Pantalla de login de xrdp servida por el Web; el inicio de sesión falló ("login failed for display 0") | TEST-09, TEST-17, TEST-18 | Aprobada |
| T08 | Jump → Web SSH | Jump → Web | PuTTY | Sesión | Sesión `webadmin` | TEST-08 | Aprobada |
| T09 | Acceso RemoteApp | Cliente → RD Web | Navegador | Login y aplicaciones | Login y aplicaciones | RDS-08–RDS-12 | Aprobada |
| T10 | RemoteApp Web Client | Cliente → RD Web | `/RDWeb/webclient` | Cliente HTML5 | RD Web Access clásico | RDS-08 | Aprobada |
| T11 | Básico: solo Firefox | `usr_normal` | RD Web | 1 icono | 1 icono  | RDS-11/12 | Aprobada |
| T12 | Privilegiado: 3 apps | `usr_priv` | RD Web | 3 iconos | 3 iconos | RDS-09 | Aprobada |
| T13 | Básico SSH → Jump | Emely → 10.25.97.106 | Log del FortiGate + `Test-NetConnection` -Port 22 | Deny | Deny: policy violation (5 eventos) y fallo de TCP 22 | TEST-10, TEST-15, TEST-16 | Aprobada |
| T14 | Básico SSH → Web | Emely → 10.25.97.114 | `Test-NetConnection` -Port 22 | Deny | SSH falla con origen 10.25.98.10 | TEST-15 | Aprobada |
| T15 | Puerto no autorizado Jump → Web | Jump → Web:445 | `Test-NetConnection` | Fallo con log | Fallo, sin log; puerto cerrado en el Web | TEST-11 | Aprobada |
| T16 | Cliente LAN → Web | 10.25.6.20 → Web | `Test-NetConnection`, `ping` | Fallo | Fallo| TEST-12/13 | Aprobada |
| T17 | Sistema de Caja | Jump → Web | Navegador | Aplicación de caja | Página Apache por defecto | TEST-06, TEST-07 | aprobada |
| T18 | Básico RDP directo al Jump | Emely → Jump:3389 | `mstsc` | -- | - | — | Aprobada |
| T19 | Usuarios → redes no autorizadas | Varios | Pruebas dirigidas | Denegado | - | — | Aprobada |

**Totales:** 6 Aprobadas · 8 Parciales · 2 No concluyentes · 3 Pendientes (T17, T18, T19).
