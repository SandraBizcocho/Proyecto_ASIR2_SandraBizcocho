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

Para el taller **Triana Motor** he seleccionado un stack tecnológico basado íntegramente en Software Libre (FOSS) para garantizar la soberanía tecnológica y reducir costes de licencias.

- **Sistema Operativo Host:** Debian 12 (Bookworm) por su estabilidad y soporte a largo plazo.
- **Orquestación:** Docker Engine con Docker Compose para la fase inicial y escalabilidad futura a Kubernetes.
- **Seguridad de Red:** IPTables/NFTables en el servidor Debian para gestionar el tráfico entre las 3 interfaces (WAN, LAN, DMZ).
- **Infraestructura Cloud:** AWS (Capa gratuita) con instancias EC2 para la redundancia y base de datos externa.
- **Túnel Seguro:** WireGuard para la interconexión cifrada entre la sede física y AWS.

[⬆️ Volver al índice de apartados](#índice-de-apartados)

---

# **2. Diseño lógico y físico de la infraestructura**

El diseño se basa en la segmentación de red para proteger los datos de los clientes del taller.

**Diseño Físico (Topología de red)El servidor central cuenta con 3 tarjetas de red (NICs) físicas o virtualizadas para aislar los entornos de trabajo:NIC 1 (WAN): Conexión a Internet (DHCP dinámico para asegurar portabilidad entre casa/clase).NIC 2 (LAN): Red interna para el PC de Administración y el terminal de operarios.NIC 3 (DMZ): Red aislada para los contenedores de servicios web y base de datos.Diseño Lógico (Plan de IP Estáticas)ElementoInterfazDirección IPServidor Debian (Gateway)eth1 (LAN)192.168.10.1Servidor Debian (Gateway)eth2 (DMZ)172.16.0.1PC Administración (Grafana)LAN192.168.10.10Contenedor Web App CitasDMZ172.16.0.10Contenedor PostgreSQLDMZ172.16.0.20


## Enlaces a recursos de la unidad

- [Documentos de la unidad](./documentos/)
- [Diagramas e imágenes](./img/)

## Bibliografía / Webgrafía
- Autor1, Título del libro o artículo, Editorial/Año.
- Sitio web oficial: [Enlace](https://www.ejemplo.com)
- Tutoriales y guías recomendadas: [Enlace](https://www.ejemplo2.com)
