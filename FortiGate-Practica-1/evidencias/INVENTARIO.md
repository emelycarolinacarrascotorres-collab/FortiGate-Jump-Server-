# Inventario de evidencias

Los originales se conservan sin modificar. Antes de publicar, crear copias redactadas de las capturas con nombres completos de usuarios de dominio (AD-02, AD-03, AD-04) y de la PSK si apareciera.

| Archivo | Componente | Contenido | Requisito | Estado |
|---|---|---|---|---|
| fortigate/FW-01-interfaces.png | FortiGate | Interfaces | Red | Demostrado |
| fortigate/FW-02-ruta-estatica.png | FortiGate | Ruta por defecto | Red | Demostrado |
| fortigate/FW-03-objetos-address.png | FortiGate | Objetos | Políticas | Demostrado |
| fortigate/FW-04-servicios-personalizados.png | FortiGate | Servicios | Políticas | Demostrado |
| fortigate/FW-05-politicas-seguridad.png | FortiGate | Políticas | Políticas | Demostrado |
| usuarios/FW-06-grupos-usuarios.png | FortiGate | Grupos | Perfiles | Demostrado |
| usuarios/FW-07-usuarios-locales.png | FortiGate | Usuarios | Perfiles | Demostrado |
| usuarios/AD-01…04 | Active Directory | Grupos RA y miembros | Perfiles | Parcial |
| vpn/VPN-01-config-tunel-vpn-remote.png | FortiGate | Resumen del túnel | VPN | Parcial |
| vpn/VPN-02-forticlient-conectado.png | Cliente | VPN conectada | VPN | Demostrado |
| vpn/VPN-03-monitor-ipsec.png | FortiGate | Monitor IPsec | VPN | Demostrado |
| vpn/VPN-04-ip-cliente-vpn.png | Cliente | IP y adaptadores | VPN / DHCP | Demostrado |
| red/RED-01-topologia-gns3.png | GNS3 | Topología | Arquitectura | Demostrado |
| red/RED-02-ipconfig-jump.png | Jump | IP | Red | Demostrado |
| red/RED-03-ip-web-server.png | Web | IP | Red | Demostrado |
| red/RED-04-puertos-escucha-web.png | Web | Puertos 22, 80, 443 | Servicios | Demostrado |
| red/RED-05-xrdp-3389-web.png | Web | xrdp en 3389 | RDP | Demostrado |
| red/RED-06-usuario-webadmin.png | Web | Usuario `webadmin` | SSH | Demostrado |
| jump-server/RDS-01…03 | Jump | RDS y colección | RemoteApp | Demostrado |
| remoteapp/RDS-04…13 | Jump / RD Web | Asignaciones, login, iconos | RemoteApp | Parcial |
| pruebas-permitidas/TEST-01…08 | Varios | Pruebas exitosas | Pruebas | Ver matriz |
| pruebas-denegadas/TEST-10 | FortiGate | Deny SSH Jump | Restricciones | Demostrado |
| pruebas-denegadas/TEST-11…13 | Varios | Fallos no concluyentes | Restricciones | No concluyente |

## Duplicados y exclusiones
- Capturas de pantalla duplicadas (misma imagen con nombre descriptivo y nombre de fecha): 8 pares; se conserva la versión descriptiva.
- `…214949.png` es un recorte de `…215014.png` (RED-06); se conserva una.
- `…184349.png` y `…212156.png` son la misma pantalla de inicio de sesión (RDS-08); se conserva una.
- `…200209.png` (pregunta de examen sobre GPS): **no pertenece a la práctica; excluida**.

## Segundo lote (10/10/2026)
| Archivo | Contenido | Estado |
|---|---|---|
| pruebas-denegadas/TEST-14 | VPN → Web 443/22/ping con origen 10.25.98.10 | Parcial (falta log) |
| pruebas-denegadas/TEST-15 | SSH al Jump y al Web con origen 10.25.98.10 | Parcial |
| pruebas-denegadas/TEST-16 | Log de Deny en DENY-SSH-BASICO-JUMP | Demostrado |
| pruebas-permitidas/TEST-09 | mstsc con destino 10.25.97.114 | Demostrado |
| pruebas-permitidas/TEST-17 | Login de xrdp en web-server-lab-1 | Demostrado |
| pruebas-permitidas/TEST-18 | Login RDP fallido | Fallo documentado |
| pruebas-permitidas/TEST-19 | Log BASICO-to-JUMP | Demostrado |
| remoteapp/RDS-14, RDS-15 | Sesiones usr_priv y usr_normal en COL-JUMP | Parcial |

## Nota sobre capturas repetidas
`Captura_de_pantalla_2026-10-10_000849.png` (nuevo recorte de la pantalla de xrdp con el escritorio vacío) corresponde al mismo evento que TEST-18; no aporta información adicional y no se incluye por separado.
