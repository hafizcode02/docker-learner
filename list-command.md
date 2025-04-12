# Showing Docker Version

```bash
docker version
```

---

# Basic Docker Command for Listing Images & Container

```bash
docker images ls -a
docker container ls -a
```

---

# Docker Download Image (Pull)

```bash
# docker pull image:version
docker pull redis:latest
```

---

# Docker Creating Container Image

```bash
# docker create --name your-container-name image:version
docker create --name nginx-service nginx:latest
```

---

# Docker Logging from Container Image

```bash
# docker logs container_name
docker logs nginx-service

# docker logs -f --timestamps container_name (realtime logging with timestamps)
docker logs -f --timestamps nginx-service
```

---

# Docker Exec Container (Access the Container Content or Running the Cli)

```bash
docker container exec -i -t nginx-service /bin/bash
```

---

# Create Docker Container Port (Port Forwarding)

```bash
# Create Container Image Nginx with port forwading (publish) in 0.0.0.0:8080
docker container create --name "nginx-service-public" --publish 8080:80 nginx:latest

# Create Container Image Nginx with port forwarding (publish) only in localhost 127.0.0.1:8070
docker container create --name "nginx-service-local" --publish 127.0.0.1:8070:80 nginx:latest
```
Why we must use the second option rather than first option, it is to make sure the service will be accessed by our local service

---

# Adding Resource Limit to Docker Container
```bash
# Creating a Limit with CPU & Memory Usage Limit
docker container create --name "small-redist-be" --publish 127.0.0.1:8811:6379 --memory 500m --cpus 0.2 redis:latest
```

---

# Adding Env & Mounting on Docker Container
```bash
docker container create \
  --name pg-bind \
  --mount type=bind,source=/home/user/pgdata,target=/bitnami/postgresql \
  -e POSTGRES_USER=myuser \
  -e POSTGRES_PASSWORD=mypassword
  -e POSTGRES_DB=mydatabase \
  -p 5433:5432 \
  postgres:latest
```

---

# Using Volume Mounting
```bash
# Create volume
docker volume create redis-data
docker container create --name "redis-be-v2" --mount "type=volume,source=redis-data,target=/data" --publish "127.0.0.1:6373:6379" redis:latest
```

---

# Docker Backup Volume
```bash
# Stop The Container want to backup the volume
docker container stop redis-be-v2
# Create the directory for saving data
mkdir backup_data
# Creating new Docker Container
docker container create --name backupnginx --mount "type=bind,source=E:\Projects\learn-stuff\docker-learner\testbackup,destination=/backup" --mount "type=volume,source=redis-data,destination=/data" nginx:latest
# Start the new Docker container
docker container start backupnginx
# Inspect the docker container file
docker container exec -i -t backupnginx /bin/bash
# Zipping the ./data folder to ./backup
cd ./backup
tar cvf /backup/backup.tar.gz /data
```
```bash
# Creating another container and directly run the command from it
docker pull ubuntu:latest
docker run --rm --name ubuntubackup --mount "type=bind,source=E:\Projects\learn-stuff\docker-learner\testbackup,destination=/backup" --mount "type=volume,source=redis-data,destination=/data" ubuntu:latest tar cvf /backup/backup.tar.gz /data
```

---

