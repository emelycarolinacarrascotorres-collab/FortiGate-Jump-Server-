# Scripts

**No existen scripts propios de esta práctica.** Toda la configuración del FortiGate se hizo por GUI, como exige el enunciado. No se incluye ningún script inventado.

## Comandos de prueba que sí aparecen en las capturas
Son comandos manuales, no scripts. Se listan para reproducibilidad.

| Dónde | Comando | Evidencia |
|---|---|---|
| Cliente (PowerShell) | `Test-NetConnection 10.25.97.106 -Port 443` y `-Port 3389` | TEST-01 |
| Cliente (PowerShell) | `Test-NetConnection 10.25.97.114 -Port 443` / `-Port 22`; `ping 10.25.97.114` | TEST-12, TEST-13 |
| Cliente (cmd / PS) | `ipconfig`, `Get-NetIPConfiguration` | VPN-04 |
| Jump (PowerShell) | `Test-NetConnection 10.25.97.114 -Port 443 / 22 / 3389 / 445` | TEST-04, TEST-11 |
| Jump (PowerShell) | `curl.exe -k -I https://10.25.97.114`; `ipconfig /all` | TEST-05, RED-02 |
| Web (shell) | `ss -tlnp \| grep -E ':22\|:80\|:443'`; `ss -tlnp \| grep 3389`; `grep '^webadmin:' /etc/passwd`; `ip a` | RED-03…06 |
