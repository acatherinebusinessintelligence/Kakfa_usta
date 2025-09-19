# 📘 Guía de Comandos Básicos: Podman + Kafka CLI

Este documento recopila los comandos esenciales para trabajar con **Podman** y **Apache Kafka**.  
Incluye ejemplos listos para copiar y pegar en la terminal.

---

## 🐙 Comandos básicos de Podman

### 🔍 Ver contenedores activos
```bash
podman ps
```
Muestra una lista de todos los contenedores que están **en ejecución**.  
Incluye el **ID del contenedor**, imagen usada, puertos expuestos, estado y nombre asignado.

---

### 📋 Ver todos los contenedores (incluidos detenidos)
```bash
podman ps -a
```
Lista tanto los contenedores en ejecución como los que ya se **detuvieron**.

---

### ⚡ Construir e iniciar servicios con Podman Compose
```bash
podman-compose up --build -d
```
- `--build`: fuerza la reconstrucción de las imágenes.  
- `-d`: ejecuta los contenedores en segundo plano (**modo detached**).  
- `up`: levanta los servicios definidos en el archivo `docker-compose.yml` (también funciona con `podman-compose.yaml`).  

---

### 🔗 Conectarse a un contenedor
```bash
podman exec -it NOMBRE_CONTENEDOR bash
```
- `-it`: abre una sesión interactiva.  
- `NOMBRE_CONTENEDOR`: el nombre o ID del contenedor que quieres abrir.  
- `bash`: abre una shell dentro del contenedor.  
Sirve para **administrar desde dentro** el contenedor (ejemplo: revisar logs, ejecutar comandos internos, etc.).

---

## 📡 Comandos básicos de Kafka (CLI dentro del contenedor)

> ⚠️ Nota: estos comandos se ejecutan dentro del contenedor de Kafka.  
Conéctate primero con:  
```bash
podman exec -it kafka bash
```

### 📌 Crear un topic
```bash
kafka-topics --create --topic mi-tema   --bootstrap-server localhost:9092   --partitions 1   --replication-factor 1
```
- `--topic`: nombre del tema.  
- `--partitions`: cantidad de particiones.  
- `--replication-factor`: factor de replicación.  
- `--bootstrap-server`: dirección del broker.

---

### 📌 Listar topics existentes
```bash
kafka-topics --list --bootstrap-server localhost:9092
```

---

### 📌 Describir un topic
```bash
kafka-topics --describe --topic mi-tema --bootstrap-server localhost:9092
```

---

### 📨 Enviar mensajes con Producer
```bash
kafka-console-producer --topic mi-tema --bootstrap-server localhost:9092
```
Después de ejecutar este comando, puedes escribir mensajes en la terminal.  
Cada línea que escribas será enviada como un mensaje al **topic**.

---

### 📥 Recibir mensajes con Consumer
```bash
kafka-console-consumer --topic mi-tema   --bootstrap-server localhost:9092   --from-beginning
```
- `--from-beginning`: permite leer todos los mensajes desde el inicio del topic.

---

✅ Con estos comandos puedes administrar contenedores con **Podman** y trabajar con **Kafka** desde la CLI fácilmente.
