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

# Create Docker Container Port (Port Forwarding)

```bash
# Create Container Image Nginx with port forwading (publish) in 0.0.0.0:8080
docker container create --name "nginx-service-public" --publish 8080:80 nginx:latest

# Create Container Image Nginx with port forwarding (publish) only in localhost 127.0.0.1:8070
docker container create --name "nginx-service-local" --publish 127.0.0.1:8070:80 nginx:latest
```

Why we must use the second option rather than first option, it is to make sure the service will be accessed by our local service
