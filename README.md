# Boogeyman 3 - TryHackMe Writeup

# 📌 Introducción

Quick Logistics LLC vuelve a ser víctima del grupo Boogeyman, que en este escenario evoluciona hacia un ataque más avanzado y coordinado.
La intrusión inicia con un phishing dirigido al CEO (Evan Hutchinson), a través de un supuesto PDF que en realidad era un archivo .hta malicioso ejecutado mediante mshta.exe.

Este ejercicio expone técnicas de inicialización, persistencia, escalamiento de privilegios, movimiento lateral y compromiso total del dominio.


#🔎 Metodología de Análisis

Plataforma utilizada: Elastic Stack (ELK) con registros de Sysmon.

Enfoque: Búsqueda de procesos, conexiones de red y correlación de eventos mediante queries sobre event.provider y event.code.

Objetivo: Identificar los TTPs usados por Boogeyman y documentar IoCs.


# ⚔️ Cadena de Flujo de Eventos

Acceso inicial → Phishing con un archivo malicioso.

Ejecución → Uso de herramientas legítimas del sistema (LOLBins).

Persistencia → Creación de mecanismos que aseguran la ejecución futura del malware.

Comunicación C2 → Establecimiento de canal con infraestructura controlada por el atacante.

Escalamiento de privilegios → Abuso de procesos confiables del sistema.

Robo de credenciales → Descarga y ejecución de herramientas de volcado de credenciales.

Movimiento lateral → Uso de comandos remotos para comprometer más equipos.

Compromiso del dominio → Acceso a cuentas críticas y control total del Active Directory.


# 🧩 IoCs Relevantes

Hashes del artefacto inicial

MD5: 665D512BB2727713783B73F1B7FEB808

SHA256: 4B82CFC44029D3D8462D60322FA0DBDE20F36C9C6791FA6F9B9F6A96FE44BF09

Binarios LOLBins utilizados

mshta.exe, xcopy.exe, rundll32.exe, powershell.exe, fodhelper.exe

Persistencia

Scheduled Task

Credenciales robadas


# 📚 Aprendizajes Clave

El grupo Boogeyman evolucionó de simples persistencias (Boogeyman 1 y 2) a un ciclo completo de intrusión en Boogeyman 3.

El uso de LOLBins y técnicas de living-off-the-land facilita la evasión.

Mimikatz + Pass-the-Hash + DCSync garantizan dominio total.

La combinación de phishing, persistencia, movimiento lateral y evasión avanzada simula un ataque realista contra un SOC.


# 🏁 Conclusión

El escenario Boogeyman 3 muestra la madurez de los atacantes: desde un phishing inicial, pasando por persistencia, escalamiento y movimiento lateral, hasta llegar al compromiso total del Domain Controller (DC01).
Este ejercicio evidencia cómo un adversario persistente puede aprovechar técnicas legítimas (LOLBins), robar credenciales y pivotar entre sistemas hasta tomar control absoluto de la infraestructura corporativa.


# 📖 Referencias  

- [MITRE ATT&CK® Framework](https://attack.mitre.org/)  
- [LOLBAS Project (Living Off The Land Binaries)](https://lolbas-project.github.io/)  
- [Sysinternals Suite](https://learn.microsoft.com/en-us/sysinternals/)  
- [Mimikatz Official GitHub](https://github.com/gentilkiwi/mimikatz)  
- [Windows Event Logging Cheat Sheet](https://www.mandiant.com/resources/windows-event-logging)  
- [TryHackMe - Boogeyman Room](https://tryhackme.com)  
