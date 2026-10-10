# 01 · Introducción y objetivos

## Propósito
Documentar una infraestructura de seguridad de red ya implementada en GNS3, basada en un FortiGate, una VPN IPsec de acceso remoto y un Jump Server con RemoteApp. El repositorio presenta la configuración observada, las pruebas ejecutadas y su nivel de respaldo.

## Alcance
- Incluye: interfaces, rutas, objetos, servicios y políticas del FortiGate; VPN; Jump Server (RDS/RemoteApp); Web Server; Cisco-SRV (DHCP/NAT); ISP.
- No incluye: configuración por CLI del FortiGate. La práctica exige GUI, por lo que las evidencias del firewall son capturas de la interfaz gráfica. **No existe un `running-config` del FortiGate** y no se publica ninguno.

## Requisitos de la práctica y dónde se atienden

| Requisito | Documento |
|---|---|
| Segmentación y direccionamiento (/29 servidores, /25 usuarios, VLAN 10, DHCP) | [03](03-direccionamiento-y-red.md) |
| VPN Remote-Site | [04](04-vpn-remote-site.md) |
| VPN solo hacia el Jump Server | [06](06-politicas-seguridad.md), [07](07-pruebas-validacion.md) |
| Jump → Web solo por HTTPS, RDP, SSH | [06](06-politicas-seguridad.md), [07](07-pruebas-validacion.md) |
| RemoteApp y Web Client por perfil | [05](05-jump-server-y-remoteapp.md) |
| Usuario sin privilegios: solo aplicación web y SSH denegado | [05](05-jump-server-y-remoteapp.md), [07](07-pruebas-validacion.md) |
| Evidencias, diagramas, configs y video | README, [`evidencias/`](../evidencias/INVENTARIO.md) |

## Principio de documentación
Cada afirmación se apoya en una captura o archivo. Lo que no tiene evidencia se marca **Pendiente**. Los estados usados son: *Aprobada*, *Parcial*, *Ejecutada, no concluyente* y *Pendiente*.

## Los tres controles que se evalúan por separado
1. **Publicación RemoteApp**: qué iconos ve cada usuario.
2. **Permisos del usuario**: pertenencia a grupos de AD y del FortiGate.
3. **Reglas de red del FortiGate**: qué tráfico se permite o se deniega.

Que una aplicación esté publicada o no, no prueba por sí sola una restricción de red.
