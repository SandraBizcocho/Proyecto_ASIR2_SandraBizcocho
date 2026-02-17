[Volver al índice general](../README.md)
# UD2 – Diseño técnico de la infraestructura empresarial segura y automatizada

![Debian](https://img.shields.io/badge/Debian-A81D33?style=for-the-badge&logo=debian&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=for-the-badge&logo=kubernetes&logoColor=white)
![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
![Grafana](https://img.shields.io/badge/grafana-%23F46800.svg?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=Prometheus&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)


## Índice de apartados

- [ ] **1. Recopilación de información técnica**
- [ ] **2. Diseño lógico y físico de la infraestructura**
- [ ] **3. Definición de objetivos y fases del proyecto**
- [ ] **4. Recursos y presupuesto**
- [ ] **5. Documentación técnica**


# **1. Recopilación de información técnica**

Para el taller **Triana Motor** he seleccionado un stack tecnológico basado íntegramente en **Software Libre (FOSS) y 100% Linux** para maximizar la soberanía tecnológica y reducir costes de licencias.

- **Sistema Operativo Host:** Debian 12 (Bookworm) por su estabilidad crítica para orquestación de contenedores y soporte a largo plazo.
- **Orquestación:** Docker Engine con Docker Compose para el despliegue de microservicios aislados en la fase inicial y escalabilidad futura a Kubernetes.
- **Conectividad Segura: Wireguard** para establecer un túnel VPN cifrado entre la sede física de Triana y la nube.
- **Infraestructura Cloud:** AWS (Capa gratuita) para la redundancia de datos y servicios externos mediante instancias EC2.
- **Servicios de Red:** Agentes de monitorización y un servicio de DHCP failover para la gestión dinámica de IPs en la LAN del taller.

[⬆️ Volver al índice de apartados](#índice-de-apartados)

---

# **2. Diseño lógico y físico de la infraestructura**

La arquitectura se diseña bajo el principio de **segmentación de red** para proteger los datos de los clientes del taller.

**Diseño Físico (Topología de red)** 
El servidor central actuará como Gateway/Firewall con 3 tarjetas de red (NICs) físicas/virtualizadas para aislar los entornos de trabajo:
**1. NIC 1 (WAN):** Interfaz en modo **DHCP** (adaptador puente). Permite la portabilidad entre casa/clase).
**2. NIC 2 (LAN):** Red interna para el PC de Administración y el terminal de operarios.
**3. NIC 3 (DMZ):** Red aislada para los contenedores de servicios web y base de datos.


**Diseño Lógico (Plan de IP Estáticas)**

Elemento                       Interfaz      Dirección IP
__________________________________________________________
Servidor Debian (Gateway)      eth1(LAN)     192.168.10.1
Servidor Debian (Gateway)      eth2(DMZ)     172.16.0.1
PC Administración (Grafana)       LAN        192.168.10.10
Contenedor Web App Citas          DMZ        172.16.0.10
Contenedor PostgreSQL             DMZ        172.16.0.20

[⬆️ Volver al índice de apartados](#índice-de-apartados)

---

# **3. Definición de objetivos y fases del proyecto**

El objetivo principal es digitalizar la gestión de citas de Triana Motor mediante una infraestructura híbrida segura.

* **Fase 1: Despliegue Local (On-premise):** Instalación de Debian 12, configuración de las 3 redes y el stack de Docker Compose.
* **Fase 2: Monitorización y Control:** Implementación de Grafana en el PC de Admin para supervisar el rendimiento (CPU, RAM, Disco).
* **Fase 3: Hibridación Cloud:** Configuración del túnel VPN y despliegue de la base de datos de respaldo en AWS.
* **Fase 4: Pruebas y Seguridad:** Auditoría de firewall y simulación de fallos de red.

[⬆️ Volver al índice de apartados](#índice-de-apartados)

---

# **4. Recursos y presupuesto**

Siguiendo la filosofía "Hibridofoss", el presupuesto se reduce a la inversión en hardware, ya que el software no tiene costes de licencia directa.

* **Hardware:** Servidor físico (o VM con recursos asignados: 4GB RAM, 2 vCPUs, 40GB SSD).
* **Software (Gratuito):** Debian Linux, Docker, PostgreSQL, Grafana, WireGuard.
* **Servicios Cloud:** AWS Free Tier (Coste $0 durante los primeros 12 meses).

[⬆️ Volver al índice de apartados](#índice-de-apartados)

---

# **5. Documentación técnica**

Toda la evolución del proyecto, archivos de configuración (YAML, scripts de red) y manuales de usuario se centralizarán en este repositorio de GitHub. Se utilizará el estándar de la rúbrica para asegurar la claridad y rigor técnico en cada commit.


## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

## Bibliografía / Webgrafía
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)
