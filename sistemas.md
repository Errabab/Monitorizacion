# Sistemas de monitorización
Los sistemas de monitorización son herramientas que seutilizan  para supervisar el estado y el rendimiento de los equipos y servicios en una infraestructura IT. Permiten detectar problemas, analizar tendencias y garantizar el funcionamiento óptimo de servidores, redes y aplicaciones. Estas herramientas recopilan métricas y datos en tiempo real, ofreciendo visualizaciones y alertas que ayudan al administrador.

## INSTALACIONES NECESARIAS PREVIAS
Antes de implementar estas herramientas, es fundamental preparar el entorno con las siguientes instalaciones básicas:

- **Sistema operativo base**: Asegúrate de tener un servidor Linux actualizado, como Ubuntu o Debian.

- **Acceso root o sudo**: Requerido para la instalación y configuración de las herramientas.

- **Herramientas de gestión**: Instalar paquetes como **prometheus** , **gestor de paquetes APT**, **paquetes ppa**

    ### Comandos para las instalaciones necesarias.
```bash 
    #Instaalr prometheus
    apt install prometheus

    #gestor de paquetes APT( permite descargar paquetes con https )
    apt install -y apt-transport-https

    #paquetes ppa(permite descar paquetes de terceros)
    apt install -y software-properties-common wget

    #Para instalar grafana 
    wget -q -O - https://packages.grafana.com/gpg.key | apt-key add 
    
    echo "deb https://packages.grafana.com/oss/deb stable main" | tee -a /etc/apt/sources.list.d/grafana.list
```

## HERRAMIENTAS DE MONITORIZACIÓN
### Node Exporter
**Node Exporter** es un agente que recopila métricas del sistema, como uso de CPU, memoria, disco y red. Es parte de Prometheus y está diseñado para integrarse fácilmente con esta herramienta de monitorización.

![.](/img/M19.png)
![.](/img/M21.png)
![.](/img/M22.png)



### Grafana
**Grafana** es una plataforma de visualización que permite crear paneles interactivos y personalizables a partir de datos recopilados por herramientas como Prometheus o Node Exporter. Es conocida por su flexibilidad y capacidad de integración con múltiples fuentes de datos.

![.](/img/M20.png)


### Zabbix
**Zabbix** es una plataforma de monitorización de código abierto que ofrece supervisión de redes, servidores, aplicaciones y servicios en tiempo real. Soporta la recolección de métricas mediante agentes, protocolos como SNMP y otras integraciones.

![.](/img/M23.png)


### Nagios
**Nagios** es una herramienta de monitorización que se centra en el seguimiento de la disponibilidad y el estado de sistemas y servicios. Permite configurar alertas que notifican de problemas en tiempo real y ofrece un enfoque modular mediante plugins.

![.](/img/M24.png)

