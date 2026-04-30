# EJERCICIO-EN-CLASE-SOFWARE-GESTI-N-Y-AN-LISIS-DE-REDES-

📡 Sistema de Gestión y Análisis de Redes Convergentes
📌 Descripción del Proyecto

Este proyecto consiste en el desarrollo de un sistema modular que funciona como asistente para ingenieros de redes, enfocado en la gestión, configuración y análisis de redes convergentes (voz, video y datos).

El sistema permite generar configuraciones para equipos de red, monitorear el rendimiento en tiempo real y analizar tráfico sensible como VoIP y video streaming.

🎯 Objetivo General

Diseñar e implementar una aplicación que permita:

Generar configuraciones para dispositivos de red (Cisco y Huawei)
Visualizar métricas de red en tiempo real
Analizar tráfico de voz y video
Gestionar VLANs y políticas de calidad de servicio (QoS)
Aplicar listas de control de acceso (ACLs)
⚙️ Tecnologías Utilizadas
Python (Backend)
FastAPI (API REST y documentación en /docs)
HTML / CSS / JS (Interfaz web si aplica)
Simulación de tráfico de red
Protocolos:
RTP (voz)
RTSP (video)
SNMP (simulado)
🧩 Arquitectura del Sistema

El sistema está diseñado de forma modular:

🔹 1. Módulo de Configuración Multi-Vendor

Genera comandos para dispositivos:

Cisco (IOS)
Huawei (VRP)

Incluye:

VLAN Voice
QoS (priorización de tráfico)
ACLs estándar y extendidas
🔹 2. Módulo de Dashboards

Visualiza métricas como:

📶 Disponibilidad (ping / SNMP simulado)
📊 Rendimiento:
Ancho de banda
Jitter
Pérdida de paquetes
⚠️ Eventos:
Logs
Alertas por umbrales
🔹 3. Analizador de Tráfico en Tiempo Real

Permite analizar tráfico multimedia:

Voz (RTP)
Video (RTSP / RTP)

Métricas calculadas:

MOS (Mean Opinion Score)
Jitter
Delay
Pérdida de paquetes
🔹 4. Gestión de VLAN Voice

Configuración automática de:

Puertos access/trunk
Prioridad CoS
Marcado DSCP
🔹 5. Listas de Control de Acceso (ACLs)

Permite:

Filtrar tráfico por IP
Controlar protocolos (TCP/UDP)
Permitir servicios específicos (SIP, RTP)
🌐 API del Sistema

El sistema expone una API documentada en:

http://127.0.0.1:8000/docs#/

Desde allí se pueden probar endpoints como:

Generación de configuraciones
Consulta de métricas
Simulación de tráfico
Gestión de eventos
📂 Estructura del Proyecto (Ejemplo)
network_assistant/
│
├── app/
│   ├── main.py
│   ├── routes/
│   ├── services/
│   ├── models/
│   └── utils/
│
├── data/
├── logs/
├── templates/
├── static/
│
├── requirements.txt
└── README.md
🚀 Instalación y Ejecución
1. Crear entorno virtual
python3 -m venv venv
2. Activar entorno
source venv/bin/activate
3. Instalar dependencias
pip install -r requirements.txt
4. Ejecutar servidor
uvicorn app.main:app --reload
5. Acceder a la API

Abrir en el navegador:

http://127.0.0.1:8000/docs#/
🧪 Simulación

El sistema no requiere dispositivos reales, ya que:

Genera tráfico sintético
Simula métricas de red
Permite pruebas controladas
📈 Resultados Esperados
Automatización de configuraciones de red
Monitoreo eficiente en tiempo real
Mejora en análisis de calidad de servicio (QoS)
Simulación realista de entornos de red
🔮 Mejoras Futuras
Integración con dispositivos reales (SSH / Netmiko)
Base de datos (PostgreSQL / MongoDB)
Autenticación de usuarios
Visualización avanzada (Grafana)
IA para detección de anomalías
