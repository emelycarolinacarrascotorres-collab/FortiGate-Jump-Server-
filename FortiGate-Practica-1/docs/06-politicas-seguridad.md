# 06 · Políticas de seguridad

## Objetos
![Objetos](../evidencias/fortigate/FW-03-objetos-address.png)
*FW-03. Direcciones: H-JUMP 10.25.97.106/32, H-WEB 10.25.97.114/32, NET-JUMP 10.25.97.104/29, NET-VPN-POOL 10.25.98.10–10.25.98.50.*

No existe un objeto para la red del Web (10.25.97.112/29); se usa solo el host H-WEB.

## Servicios personalizados
![Servicios](../evidencias/fortigate/FW-04-servicios-personalizados.png)
*FW-04.*

| Servicio | Protocolos | Uso |
|---|---|---|
| SVC-JUMP-ACCESS | HTTPS, RDP | VPN → Jump |
| SVC-JUMP-TO-WEB | HTTP, HTTPS, RDP, SSH | Jump → Web |

**Desviación respecto al requisito.** La práctica exige HTTPS, RDP y SSH. SVC-JUMP-TO-WEB.

## Políticas
![Políticas](../evidencias/fortigate/FW-05-politicas-seguridad.png)
*FW-05. Orden de evaluación, de arriba abajo.*

| # | Nombre | Desde → Hacia | Origen | Destino | Servicio | Acción | Bytes |
|---|---|---|---|---|---|---|---|
| 1 | DENY-SSH-BASICO-WEB | VPN-REMOTE → port2 | GRUP-BASIC + NET-VPN-POOL | H-WEB | SSH | DENY | 0 B |
| 2 | DENY-SSH-BASICO-JUMP | VPN-REMOTE → port4 | GRUP-BASIC + NET-VPN-POOL | H-JUMP | SSH | DENY | 260 B |
| 3 | BASICO-to-JUMP | VPN-REMOTE → port4 | GRUP-BASIC + NET-VPN-POOL | H-JUMP | SVC-JUMP-ACCESS | ACCEPT | 2.15 MB |
| 4 | PRIV-to-JUMP | VPN-REMOTE → port4 | GRUP-PRIV + NET-VPN-POOL | H-JUMP | SVC-JUMP-ACCESS | ACCEPT | 448 B |
| 5 | JUMP-to-WEB | port4 → port2 | H-JUMP | H-WEB | SVC-JUMP-TO-WEB | ACCEPT | 42.76 kB |
| — | Implicit Deny | any → any | all | all | ALL | DENY | 20.72 kB |

Las políticas ACCEPT tienen NAT deshabilitado y perfil `no-inspection`. Los números de la primera columna son el orden visual; los ID reales que muestra el log son `DENY-SSH-BASICO-JUMP (1)`, `BASICO-to-JUMP (3)` y `JUMP-to-WEB (5)`.

