# Configuraciones

| Archivo | Dispositivo | Propósito | Procedencia | Seguridad |
|---|---|---|---|---|
| `equipo-red/ISP-running-config.txt` | ISP (Cisco IOS 15.2) | Enlaces /30, NAT overload, salida a 192.168.42.0/24 | `show run` | Sin secretos. Publicado sin cambios |
| `equipo-red/CISCO-SRV-running-config.redactado.txt` | CISCO-SRV (R1) | VLAN 10, DHCP, NAT, SSH v2 | `show run` (`Running-Config_R1.txt`) | **Redactado** |
| `fortigate/` | FortiGate | — | — | **No hay running-config del FortiGate**; la práctica exige GUI. Evidencias en `evidencias/fortigate/` |

Fecha y versión exacta de las configuraciones: no constan en los archivos.

## Cambios hechos al archivo del Cisco
| Línea original | Cambio |
|---|---|
| `enable secret 5 <hash>` | Hash sustituido por `<HASH-REDACTADO>` |
| `username Admin privilege 15 secret 5 <hash>` | Hash sustituido por `<HASH-REDACTADO>` |
| `banner motd` con nombre y matrícula | Nombre y matrícula sustituidos |

El original **no** se sube: guardarlo localmente en `configs/equipo-red/originales/` (excluido por `.gitignore`). Aunque estos hashes son MD5 (tipo 5) y no contraseñas en claro, se recomienda cambiarlas si el repositorio es público. Estos archivos reflejan el momento del `show run` y no se asume que sean el estado actual.
