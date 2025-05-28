# 🐝 HoneyX – Honeypot Distribuido para TFM

**HoneyX** es un sistema honeypot distribuido desarrollado como parte de un Trabajo de Fin de Máster (TFM). Su objetivo es simular servicios vulnerables para atraer posibles atacantes y registrar sus actividades. El sistema está dividido en dos componentes principales:

- **Honeypot**: Simula servicios vulnerables y recopila datos de posibles intrusiones.
- **Monitorización**: Analiza y visualiza los datos recopilados mediante herramientas como Grafana y Prometheus.

---

## 📁 Estructura del Proyecto

.
├── honeypot/
│ ├── apache/
│ ├── fakessh/
│ ├── mysql/
│ ├── node_exporter/
│ ├── proftpd/
│ ├── prometheus/
│ └── docker-compose.yaml
├── monitor/
│ ├── grafana/
│ ├── loki/
│ ├── promtail/
│ └── docker-compose.yaml
├── scripts_honeypot/
│ └── run_all.sh
├── scripts_monitor/
│ └── run_all.sh
├── web_test/
├── 00_run_all_honeypot.sh
├── 00_run_all_monitor.sh
└── README.md

---

## ⚙️ Servicios Simulados

### 🔐 Honeypot

- **Apache** – Servidor web vulnerable.
- **ProFTPD** – Servidor FTP.
- **FakeSSH** – Simulación de servicio SSH para detectar escaneos o intentos de acceso.
- **MySQL** – Base de datos simulada vulnerable.
- **Prometheus** – Sistema de monitorización.
- **Node Exporter** – Exportador de métricas del sistema para Prometheus.

### 📊 Monitorización

- **Grafana** – Panel de visualización de logs y métricas.
- **Loki** – Sistema de gestión centralizada de logs.
- **Promtail** – Recolector y etiquetador de logs que los envía a Loki.

---

## 🚀 Cómo ponerlo en marcha

### 🔽 1. Clonar el repositorio

```bash
git clone https://github.com/GutiFer4/HoneyX.git
cd HoneyX
```

### 🐝 2. Desplegar la máquina Honeypot

```bash
chmod +x 00_run_all_honeypot.sh
./00_run_all_honeypot.sh

cd honeypot
docker-compose up -d --build
```

### 📈 3. Desplegar la máquina de Monitorización

```bash
chmod +x 00_run_all_monitor.sh
./00_run_all_monitor.sh

cd monitor
docker-compose up -d --build
```


## 🌐 Cómo acceder a Grafana

Una vez desplegado el entorno de monitorización, accede a Grafana desde tu navegador web:

```cpp
http://<IP_DE_LA_MÁQUINA_MONITORIZACIÓN>:3000
```

Usuario: admin
Contraseña: admin

🔐 Se recomienda cambiar la contraseña por defecto tras el primer inicio de sesión.

## Logs y Métricas

Los servicios simulados generan logs que se almacenan en volúmenes locales dentro de la máquina honeypot.

Promtail los recolecta y envía a Loki, donde se almacenan y están disponibles para consulta.

Las métricas del sistema (uso de CPU, memoria, etc.) se recogen con Node Exporter y se visualizan en Grafana mediante Prometheus.

## ✅ Requisitos del Sistema

Docker → Instalar Docker

Docker Compose → Instalar Docker Compose

## 📬 Contacto

Autor: GutiFer4

Repositorio original: HoneyX