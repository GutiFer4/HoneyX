# 🐝 HoneyX

**HoneyX** es un sistema honeypot distribuido. Su objetivo es simular servicios vulnerables para atraer posibles atacantes y registrar sus actividades. El sistema está dividido en dos componentes principales:

- **Honeypot**: Simula servicios vulnerables y recopila datos de posibles intrusiones.
- **Monitorización**: Analiza y visualiza los datos recopilados mediante herramientas como Grafana y Prometheus.

---

## 📁 Estructura del Proyecto

```plaintext
.
├── scripts_honeypot/
│   ├── 01_setup.sh
│   ├── 02_gen_compose.sh
│   ├── 03_prometheus.sh
│   ├── 04_ftp.sh
│   ├── 05_apache.sh
│   ├── 061_sql_init.sh
│   └── 06_mysql.sh
|   └── 07_promtail.sh
|   └── web/
├── scripts_monitor/
│   ├── 01_setup.sh
│   ├── 02_gen_compose
│   ├── 03_loki.sh
│   └── 04_grafana.sh
|   └── antiguo_grafana.json
|   └── apache_grafana.json
├── web_test/
├── 00_run_all_honeypot.sh
├── 00_run_all_monitor.sh
└── README.md
```

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