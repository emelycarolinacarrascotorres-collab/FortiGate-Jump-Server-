# Matriz de direccionamiento IP

| Dispositivo | Interfaz | Dirección | Red | Origen del dato |
|---|---|---|---|---|
| ISP | Gi1/0 | 20.25.6.1 | 20.25.6.0/30 | config ISP |
| ISP | Gi2/0 | 20.25.97.1 | 20.25.97.0/30 | config ISP |
| ISP | Gi3/0 | 192.168.42.20 | 192.168.42.0/24 | config ISP |
| CISCO-SRV | Gi1/0 | 20.25.6.2 | 20.25.6.0/30 | config Cisco |
| CISCO-SRV | Gi2/0.10 (VLAN 10) | 10.25.6.1 | 10.25.6.0/25 | config Cisco |
| FortiGate | port1 (WAN) | 20.25.97.2 | 20.25.97.0/30 | FW-01 |
| FortiGate | port4 (LAN Jump) | 10.25.97.105 | 10.25.97.104/29 | FW-01 |
| FortiGate | port2 (LAN Web) | 10.25.97.113 | 10.25.97.112/29 | FW-01 |
| FortiGate | port3 (MGMT) | 192.168.98.1 | 192.168.98.0/24 | FW-01 |
| Jump Server | Ethernet0 2 | 10.25.97.106 | 10.25.97.104/29 | RED-02 |
| Web Server | eth0 | 10.25.97.114 | 10.25.97.112/29 | RED-03 |
| Cliente | Ethernet0 2 (DHCP) | 10.25.6.20 | 10.25.6.0/25 | VPN-04 |
| Cliente | Adaptador Fortinet (túnel) | 10.25.98.10 | pool 10.25.98.10–50 | VPN-02 |
| FortiGate | Gateway por defecto | 20.25.97.1 | — | FW-02 |
| CISCO-SRV | Gateway por defecto | 20.25.6.1 | — | config Cisco |
| ISP | Gateway por defecto | 192.168.42.1 | — | config ISP |

**Datos no verificados:** gateway del Web Server; IP de `windows10-1` conectado al FortiGate; DNS del Jump hacia exterior.
**Pool DHCP:** 10.25.6.0/25 con .1–.10 excluidas (config Cisco).
