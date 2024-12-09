
# Monitorización de Sistemas 

## Introducción
Este repositorio explica paso a paso cómo realizar ejercicios prácticos de monitorización en **sistemas Linux**. Se muestran comandos esenciales para analizar procesos que consumen más recursos y evaluar el uso del espacio en disco. Cada comando incluye una descripción detallada y ejemplos prácticos, lo que facilita su comprensión y aplicación.

## Objetivo
- Obtener información sobre los procesos que más consumen recursos del sistema.
- Analizar el espacio ocupado por directorios específicos.

## Top 5 procesos que más  CPU consumen
Este comando muestra los 5 procesos que más CPU están consumiendo en el sistema, junto con información clave:

- **ps -eo**: Muestra una lista personalizada de procesos.
- **pid**: ID del proceso.
- **%cpu**: Porcentaje de CPU usado.
- **%mem**: Porcentaje de memoria usada.
- **time**: Tiempo total de CPU utilizado.
- **comm**: Nombre del comando que ejecuta el proceso.
- **--sort=-%cpu**: Ordena los resultados en orden descendente según el uso de CPU.
- **head -n 6**: Muestra las primeras 6 líneas (encabezado + 5 procesos).

### Comando Utilizado

```bash

ps -eo pid,%cpu,%men,time,comm --sort=-%cpu | head -n 6

```
![img](/img/M1.png)

## Uso de Memoria con el Comando free

- ***free***:
    Muestra información sobre el uso de la memoria del sistema (RAM y swap) en kilobytes.

    Salidas importantes:

    - **total**: Memoria total disponible.
    - **used**: Memoria utilizada.
    - **free**: Memoria libre.

- ***free -h***:
    Igual que free, pero muestra los valores en un formato legible para humanos (GB, MB, etc.).
- ***free -s 3***:
    Ejecuta el comando free de forma continua, actualizando cada 3 segundos.
    - Útil para monitorizar cambios en el uso de memoria en tiempo real.
    Para detenerlo: Usa Ctrl + C.

### Comando Utilizado

```bash
free 
free -h
free -s3

```

![img](/img/M2.png)

## Análisis del Espacio en Disco con los Comandos df y du

- ***df -h***

    Muestra el uso de espacio en disco de todos los sistemas de archivos montados, con tamaños legibles para humanos (GB, MB, etc.).

- ***df -h /***

    Similar al anterior, pero muestra el espacio disponible y utilizado solo para el sistema de archivos donde está montado el directorio raíz (/).


- ***sudo du -hs /home:***
    Muestra el tamaño total del directorio /home, con un formato legible para humanos, utilizando sudo para obtener permisos de lectura completos sobre el directorio.

### Comando Utilizado

```bash
df -h 
df -h / 
sudo du -hs /home

```
![img](/img/M3.png)

## Monitorización de Actividad de I/O con el Comando iostat
- **iostat**:
    Muestra estadísticas de entrada/salida (I/O) de los dispositivos de almacenamiento del sistema, incluyendo el tiempo de uso del CPU y el rendimiento de los discos.

    - **Opciones comunes**:

    - **iostat -x**: Muestra información más detallada sobre el rendimiento de los discos, como el tiempo de espera, la tasa de lectura/escritura, y el uso del disco.
    - **iostat -c**: Muestra estadísticas del CPU, como el porcentaje de uso de la CPU en diferentes estados.

### Comando Utilizado

```bash

iostat
iostat -x nvme0n1
```
![img](/img/M4.png)
![img](/img/M5.png)

## Análisis de Tráfico de Red con el Comando tcpdump
- ***tcpdump***:
    Captura y muestra el tráfico de red en tiempo real, permitiendo analizar los paquetes que pasan por la red del sistema.

- ***tcpdump -i eno1***:
    Captura paquetes de red en la interfaz de red eno1, mostrando detalles de cada paquete (origen, destino, protocolo, etc.).
    Nota: Se debe especificar la interfaz de red con -i.

- ***tcpdump -i eno1 -w capturas***:
    Captura paquetes de la interfaz eno1 y los guarda en un archivo llamado capturas para su análisis posterior.
    **Nota**: El archivo se guarda en formato binario, para ser leído después con herramientas como Wireshark o dandole los permisos de lectura a root.
### Comando Utilizado

```bash
tcpdump 
tcpdump -i eno1 
tcpdump -i eno1 -w capturas

```
![img](/img/M6.png)
![img](/img/M7.png)
![img](/img/M8.png)
![img](/img/M9.png)
![img](/img/M10.png)


## Monitorización de Conexiones TCP con tcptrack
- ***tcptrack -i eno1***:
    Muestra en tiempo real las conexiones TCP activas a través de la interfaz de red eno1.
    - Proporciona información sobre el estado de cada conexión, incluyendo el origen y destino de las IPs, los puertos, el número de bytes transmitidos y el tiempo de actividad de la conexión.
    **Nota**: Es útil para monitorizar el tráfico TCP en redes en vivo.

### Comando Utilizado

```bash

tcptrack -i eno1

```

![img](/img/M11.png)
![img](/img/M12.png)

## Monitorización de Tráfico de Red con iptraf

- ***iptraf**:
    Es una herramienta de análisis de tráfico de red en tiempo real que proporciona estadísticas detalladas sobre las conexiones activas, los paquetes de red y el uso de la red.

- ***Características***:
    - Muestra estadísticas de tráfico por protocolo (TCP, UDP, ICMP, etc.).
    - Proporciona información detallada sobre las conexiones de red, incluyendo direcciones IP, puertos, y la cantidad de datos enviados/recibidos.
    - Ofrece una visualización interactiva y en tiempo real del tráfico de la red.
        **Nota**: iptraf es útil para realizar diagnósticos de red y monitorizar el uso del ancho de banda.

### Comando Utilizado

```bash

iptraf

```

![img](/img/M13.png)
![img](/img/M14.png)

## Monitorización de Ancho de Banda con bmon
- ***bmon**:
    Es una herramienta de monitorización de red que muestra el tráfico de red en tiempo real y proporciona estadísticas sobre el uso del ancho de banda de las interfaces de red.

- **Características**:
    - Muestra estadísticas detalladas sobre el tráfico de red en una interfaz, como la cantidad de datos enviados/recibidos, la tasa de transmisión y la tasa de pérdida de paquetes.
    - Soporta visualización en modo gráfico o en formato de texto.
    - Permite monitorizar múltiples interfaces de red simultáneamente.
**Nota**: bmon es útil para obtener una visión rápida y clara del rendimiento de la red y detectar problemas como la congestión o la pérdida de paquetes.

### Comando Utilizado

```bash

bmon
```
![img](/img/M15.png)
![img](/img/M16.png)


## Monitorización del Sistema con el Comando top
- ***top***:
    Es una herramienta interactiva que muestra en tiempo real los procesos que están en ejecución en el sistema, junto con estadísticas de uso de recursos.

- **Información destacada**:

    - **Uso del CPU**: Porcentaje de CPU utilizado por cada proceso.
    - **Uso de memoria**: Cantidad de memoria RAM utilizada.
    - **Tiempo de ejecución**: Tiempo activo de cada proceso.
    - **PID**: Identificador del proceso.
- ***Controles comunes***:

    - **q**: Salir de top.
    - **k**: Finalizar un proceso especificando su PID.
    - **h**: Mostrar ayuda interactiva.
    - **P**: Ordenar los procesos por uso de CPU.
    - **M**: Ordenar los procesos por uso de memoria.
**Nota**: top es esencial para la monitorización en tiempo real de los recursos del sistema y para identificar procesos problemáticos.


### Comando Utilizado

```bash

 atop

```

![img](/img/M17.png)


## Monitorización Avanzada del Sistema con el Comando htop
- ***htop***:
    Es una herramienta interactiva y visual para monitorizar procesos y recursos del sistema, que mejora la experiencia de top con una interfaz más amigable y personalizable.

- **Características principales**:

    - Muestra barras de uso de CPU, RAM y swap en tiempo real.
    - Permite navegar fácilmente entre los procesos con las teclas de flecha.
    - Soporta acciones rápidas, como finalizar procesos directamente.
    -Ofrece filtros y opciones de búsqueda para localizar procesos específicos.
- **Atajos útiles**:

    - **F3**: Buscar un proceso por nombre.
    - **F5**: Mostrar los procesos en formato de árbol (jerarquía).
    - **F9**: Finalizar un proceso seleccionándolo.
    - **F10**: Salir de htop.
**Nota**: htop es ideal para usuarios que prefieren una experiencia visual más intuitiva y necesitan herramientas avanzadas para gestionar procesos.

### Comando Utilizado

```bash

 htop

```

![img](/img/M18.png)


# Autor
    Errabab Salec Ahrime
