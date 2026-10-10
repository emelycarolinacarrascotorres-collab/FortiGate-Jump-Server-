# 08 · Conclusiones

## Resultados
- La topología, el direccionamiento y las políticas del FortiGate están respaldados por capturas de la GUI.
- La VPN IPsec se establece y el cliente alcanza el Jump Server por HTTPS y RDP.
- El Jump alcanza el Web Server por SSH y HTTPS, y la política de red coincide con el requisito (con la salvedad de HTTP).
- La publicación RemoteApp diferencia los perfiles: Firefox para ambos; PuTTY y Conexión a Escritorio remoto solo para RA-Priv.
- El bloqueo de SSH del perfil básico hacia el Jump está registrado en el firewall.

## Valoración
La arquitectura es coherente con el objetivo de la práctica y la mayor parte de la cadena está evidenciada.
