# EJERCICIO-EN-CLASE-SOFWARE-GESTI-N-Y-AN-LISIS-DE-REDES-


📡 NetAssist — Asistente de Ingeniero de Redes
🧾 Descripción del Proyecto

NetAssist es un prototipo de aplicación web desarrollado como solución al ejercicio de clase, cuyo objetivo es implementar un sistema de gestión, monitoreo y configuración para redes convergentes (voz, video y datos).

El sistema simula el comportamiento de una red empresarial y proporciona herramientas para:

Generación de configuraciones multi-vendor (Cisco y Huawei)
Monitoreo en tiempo real de métricas de red
Análisis de tráfico VoIP (RTP/RTSP)
Gestión de VLAN Voice
Creación de listas de control de acceso (ACLs)

Este proyecto es completamente standalone (HTML + JS) y utiliza datos sintéticos simulados, cumpliendo con lo planteado en el ejercicio .

🎯 Objetivos
Objetivo General

Desarrollar una aplicación modular tipo asistente de red capaz de analizar, visualizar y generar configuraciones para redes convergentes.

Objetivos Específicos
Generar configuraciones Cisco IOS y Huawei VRP
Visualizar dashboards en tiempo real
Analizar métricas de QoS (latencia, jitter, pérdida, MOS)
Implementar VLAN Voice con CoS/DSCP
Crear ACLs estándar y extendidas
Simular tráfico de red
🏗️ Arquitectura del Sistema

El sistema está compuesto por módulos independientes:

🔹 1. Dashboards de Red
Disponibilidad de hosts
Latencia promedio
Pérdida de paquetes
Ancho de banda
Gráficos dinámicos con Chart.js

✔ Datos simulados cada 1.5 segundos
✔ Visualización en tiempo real

🔹 2. Generador Multi-Vendor

Permite generar configuraciones automáticamente para:

Cisco IOS
Huawei VRP

Incluye:

VLAN Voice
QoS (priorización de tráfico)
Políticas de tráfico

Ejemplo generado:

switchport voice vlan 200
mls qos trust cos
auto qos voip cisco-phone
🔹 3. VLAN Voice

Configuración automatizada para puertos:

Modo access (PC + IP Phone)
Asignación de VLAN de datos y voz
Priorización con:
CoS
DSCP

✔ Compatible con ambos vendors
✔ Generación simultánea de configuraciones

🔹 4. ACLs (Access Control Lists)

Constructor dinámico de reglas:

Permitir/denegar tráfico
Protocolos: TCP, UDP, ICMP, IP
Filtros por:
IP origen/destino
Puertos (ej: SIP 5060, RTP)

Ejemplo:

permit udp 192.168.10.0 192.168.200.0 eq 5060
deny ip any 192.168.200.0
🔹 5. Analizador RTP / RTSP

Simulación de tráfico de voz/video con métricas QoS:

Delay
Jitter
Pérdida
MOS (Mean Opinion Score)

✔ Implementa modelo E simplificado
✔ Genera alertas cuando:

MOS < 3.6 → degradado
MOS < 2.6 → crítico
🔹 6. Histórico
Almacenamiento en localStorage
Configuraciones generadas
Logs de eventos
Exportación en JSON
🖥️ Tecnologías Utilizadas
HTML5
CSS3 (UI moderna con tema oscuro)
JavaScript (Vanilla)
Chart.js (visualización de datos)
LocalStorage (persistencia)
⚙️ Funcionamiento Interno
🔸 Simulación de red

El sistema genera métricas aleatorias:

Latencia: variación controlada
Pérdida: basada en estrés
BW: fluctuación dinámica
🔸 Cálculo de MOS

Se utiliza una aproximación del modelo E:

Considera delay, jitter y pérdida
Devuelve valor entre 1 (malo) y 4.5 (excelente)
📊 Resultados Observados

Según las pruebas visuales:

✔ Disponibilidad: 100%
✔ Latencia promedio: ~35 ms
✔ Pérdida: ~0.29%
✔ Ancho de banda: ~600–700 Mbps

El sistema muestra estados:

🟢 UP
🟡 DEG (degradado)
🔴 DOWN
📁 Estructura del Proyecto
netassist/
│── netassist.html
│── README.md
│── assets/ <img width="1845" height="984" alt="imagen" src="https://github.com/user-attachments/assets/a4f4f840-fbec-497b-a063-0949c5229545" />



<img width="1837" height="746" alt="imagen (1)" src="https://github.com/user-attachments/assets/77138908-5893-4036-8981-b7bc34c22760" />
Esta imagen muestra el módulo de Configuración (Generador multi-vendor) del sistema NetAssist.

En esta sección el usuario puede:

Definir parámetros de red como:
VLAN de datos (10)
VLAN de voz (200)
Interfaz (GigabitEthernet0/1)
DSCP (46) y ancho de banda prioritario (30%)
Asignar un nombre a la configuración

Luego, con los botones:

Generar → crea la configuración
Guardar Cisco / Huawei → almacena los comandos generados

En la parte inferior se mostrarán los resultados para Cisco IOS y Huawei VRP.

👉 En resumen, esta pantalla sirve para generar y guardar configuraciones de red compatibles con múltiples fabricantes.



<img width="1818" height="1032" alt="imagen (2)" src="https://github.com/user-attachments/assets/1d255e65-fca8-485f-9f07-f673cf92b0e6" />
Esta imagen muestra el módulo “VLAN Voice” del sistema NetAssist.

En esta pantalla se configuran parámetros para telefonía IP, como:

Tipo de puerto (PC + IP Phone)
Interfaz (ej. GigabitEthernet0/2)
VLAN de datos (10) y VLAN de voz (200)
Prioridades de tráfico (CoS 5 y DSCP 46)

Al hacer clic en “Generar Cisco + Huawei”, el sistema crea automáticamente los comandos de configuración para ambos fabricantes (Cisco IOS y Huawei VRP).

👉 En resumen, esta sección permite configurar VLAN de voz con calidad de servicio (QoS) y obtener configuraciones listas para usar en equipos de red.


<img width="1759" height="1034" alt="imagen (3)" src="https://github.com/user-attachments/assets/0a83592e-2c3d-4f03-8945-8e8c376ebe76" />
Esta imagen muestra el módulo de configuración VLAN Voice y QoS en NetAssist.

Aquí se configuran parámetros como:

Puerto de red (ej. GigabitEthernet0/2)
VLAN de datos (10) y VLAN de voz (200)
Prioridad CoS (5) y DSCP (46) para tráfico de voz

Al generar, el sistema crea automáticamente los comandos de configuración para:

Cisco IOS (lado izquierdo)
Huawei VRP (lado derecho)

Incluye configuraciones de:

VLAN Voice
QoS para priorizar voz
Políticas de tráfico

👉 En resumen, esta pantalla permite configurar tráfico de voz y obtener los comandos listos para aplicar en equipos de red.


<img width="1705" height="985" alt="imagen (4)" src="https://github.com/user-attachments/assets/0cf171e0-0a07-4a9c-9d3c-5082ace5e205" />
Esta imagen muestra el módulo de Listas de Control de Acceso (ACLs) del sistema NetAssist.

Aquí el usuario puede:

Crear reglas de acceso (permitir o denegar tráfico) según:
IP origen y destino
Protocolo (TCP/UDP/IP)
Puertos (ej. 5060, 10000 para VoIP)
Usar presets como SIP/RTP o 
agregar reglas manualmente.

En la parte inferior, el sistema genera automáticamente la configuración para:

Cisco IOS
Huawei VRP

En resumen, esta pantalla permite diseñar reglas de seguridad de red y convertirlas en comandos listos para aplicar en equipos reales.


<img width="1719" height="931" alt="imagen (5)" src="https://github.com/user-attachments/assets/5eb17ccd-3fd9-43f1-8d6b-a24d0e2595bb" />
Esta imagen muestra el módulo “Analizador RTP / RTSP” del sistema NetAssist, usado para evaluar la calidad de tráfico de voz y video.

Se presentan métricas clave en tiempo real:

MOS: 4.36 (óptimo) → indica excelente calidad de voz
Delay: 28 ms → baja latencia
Jitter: 3.9 ms → variación mínima en el retardo
Pérdida: 0.13% → casi sin pérdida de paquetes

También incluye una gráfica que muestra la evolución de estas métricas en el tiempo y un control de estrés, que permite simular condiciones de red más exigentes.

En resumen, esta pantalla sirve para analizar y monitorear la calidad del tráfico multimedia en la red.


<img width="1735" height="967" alt="imagen (6)" src="https://github.com/user-attachments/assets/1eda4272-9131-4641-b451-1a3ffe618431" />
Esta imagen muestra el módulo “Histórico” del sistema NetAssist, una consola para gestión de redes.

En esta pantalla se pueden ver dos cosas principales:

Configuraciones guardadas: actualmente no hay ninguna, pero existe la opción de exportarlas en formato JSON.
Log de eventos: un registro de las últimas acciones del sistema, como la creación de ACLs, configuración de VLAN Voice y el inicio del sistema, con fecha, hora y tipo de evento.

En resumen, es la sección donde se almacenan y visualizan las actividades realizadas dentro del sistema.

🚀 Cómo Ejecutar
Descargar el archivo netassist.html
Abrir en cualquier navegador moderno
No requiere instalación ni backend
🧠 Conclusiones
Se logró implementar un sistema modular completo según el enunciado
Se simulan correctamente métricas de red en tiempo real
La generación multi-vendor automatiza tareas reales de networking
El proyecto es escalable y puede evolucionar a:
Backend real (Python/Node.js)
Integración con dispositivos reales (SNMP, NetFlow)
Base de datos persistente
🔮 Mejoras Futuras
Integración con APIs reales de red
Autenticación de usuarios
Exportación de configuraciones a dispositivos
Machine Learning para predicción de fallos
Visualización avanzada (Grafana-like)
