# 08 · Conclusiones

## Resultados
- La topología, el direccionamiento y las políticas del FortiGate están respaldados por capturas de la GUI.
- La VPN IPsec se establece y el cliente alcanza el Jump Server por HTTPS y RDP.
- El Jump alcanza el Web Server por SSH y HTTPS, y la política de red coincide con el requisito (con la salvedad de HTTP).
- La publicación RemoteApp diferencia los perfiles: Firefox para ambos; PuTTY y Conexión a Escritorio remoto solo para RA-Priv.
- El bloqueo de SSH del perfil básico hacia el Jump está registrado en el firewall.

## Lo que aún no está demostrado
- Que la VPN **no** puede alcanzar el Web Server con tráfico real del túnel.
- El bloqueo SSH del perfil básico hacia el Web.
- Una sesión RDP Jump → Web.
- El Sistema de Caja (el Web muestra la página por defecto de Apache).

## Valoración
La arquitectura es coherente con el objetivo de la práctica y la mayor parte de la cadena está evidenciada. Mientras P1–P4 ([08](08-limitaciones-y-pendientes.md)) no se cierren con evidencia, el repositorio **no debe presentarse como cumplimiento total**. Ninguna de esas pruebas exige reconfigurar la infraestructura; requieren ejecutarse y capturarse.
