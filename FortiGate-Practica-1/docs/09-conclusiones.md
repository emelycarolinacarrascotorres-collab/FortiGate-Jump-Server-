# 09 · Conclusiones

## Resultados
- La topología, el direccionamiento y las políticas del FortiGate están respaldados por capturas de la GUI.
- La VPN IPsec se establece y el cliente alcanza el Jump Server por HTTPS y RDP.
- El Jump alcanza el Web Server por SSH y HTTPS, y la política de red coincide con el requisito (con la salvedad de HTTP).
- La publicación RemoteApp diferencia los perfiles: Firefox para ambos; PuTTY y Conexión a Escritorio remoto solo para RA-Priv.
- El bloqueo de SSH del perfil básico hacia el Jump está registrado en el firewall.

## Lo que aún no está demostrado
- El log de denegación de VPN → Web (las pruebas con origen en el túnel ya fallan, TEST-14).
- El log de la política DENY-SSH-BASICO-WEB.
- Una sesión RDP completada: el login de xrdp falló (TEST-18).
- El Sistema de Caja (el Web muestra la página por defecto de Apache).

## Valoración
La arquitectura es coherente con el objetivo de la práctica y la mayor parte de la cadena está evidenciada. Mientras P1–P4 ([08](08-alcance-y-trabajo-futuro.md)) no se cierren con evidencia, el repositorio **no debe presentarse como cumplimiento total**. Ninguna de esas pruebas exige reconfigurar la infraestructura; requieren ejecutarse y capturarse.
