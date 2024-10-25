# Instalación de Python y Bibliotecas Necesarias

## Paso 1: Instalar Python
1. Descarga e instala Python desde [python.org](https://www.python.org/downloads/).
2. Durante la instalación, asegúrate de marcar la opción **"Add Python to PATH"**.

## Paso 1.1: Instalar las Bibliotecas
Una vez que Python esté instalado, abre una terminal o línea de comandos y ejecuta los siguientes comandos para instalar las bibliotecas necesarias:

```bash
pip install tweepy kafka-python
```
## Paso 2. Instalar y configurar Apache Kafka y Zookeeper

Kafka necesita Zookeeper para funcionar, así que ambos deben estar instalados.

### Paso 2.1: Descarga Apache Kafka

- Descarga Kafka desde [apache.org](https://kafka.apache.org/downloads).
- Elige la versión binaria más reciente y descarga el archivo comprimido (`tgz` para Linux/Mac o `.zip` para Windows).

### Paso 2.2: Descomprime el archivo

- Descomprime el archivo descargado en una carpeta de tu elección.

### Paso 3: Inicia Zookeeper

- Abre una terminal y navega a la carpeta de Kafka.
- Inicia Zookeeper ejecutando el siguiente comando:

```bash
# En Linux o Mac
bin/zookeeper-server-start.sh config/zookeeper.properties

# En Windows
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```

### Paso 4: Inicia el servidor Kafka

-   Abre una nueva terminal (mantén Zookeeper ejecutándose) y navega a la carpeta de Kafka.

-   Inicia Kafka ejecutando:

```bash

# En Linux o Mac

bin/kafka-server-start.sh config/server.properties

# En Windows

.\bin\windows\kafka-server-start.bat .\config\server.properties
```
3\. Configurar un tema en Kafka

-------------------------------

Para crear el tema que usarás (en este caso `rk_hadoop`), abre otra terminal y ejecuta:

```bash

# En Linux o Mac

bin/kafka-topics.sh --create --topic rk_hadoop --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

# En Windows

.\bin\windows\kafka-topics.bat --create --topic rk_hadoop --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1`
```
4\. Ejecutar el código de Python

--------------------------------

Ahora que Kafka y Zookeeper están ejecutándose, puedes ejecutar el script de Python modificado:

```bash

python nombre_del_archivo.py
```
Asegúrate de que las credenciales de Twitter en el script sean válidas y configúralas adecuadamente. Si todo está bien configurado, el código debería conectarse a Twitter, transmitir los datos a Kafka y mostrarlos en la consola.

