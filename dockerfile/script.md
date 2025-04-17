
# FROM Instruction
docker build -t hafigo/from from

docker image ls

# RUN Instruction
docker build -t hafigo/run run

docker build -t hafigo/run run --progress=plain --no-cache

# CMD Instruction
docker build -t hafigo/command command

docker image inspect hafigo/command

docker container create --name command hafigo/command

docker container start command

docker container logs command

# LABEL Instruction
docker build -t hafigo/label label

docker image inspect hafigo/label

# ADD Instruction
docker build -t hafigo/add add

docker container create --name add hafigo/add

docker container start add

docker container logs add

# COPY Instruction
docker build -t hafigo/copy copy

docker container create --name copy hafigo/copy

docker container start copy

docker container logs copy

# .dockerignore
docker build -t hafigo/ignore ignore

docker container create --name ignore hafigo/ignore

docker container start ignore

docker container logs ignore

# EXPOSE Instruction
docker build -t hafigo/expose expose

docker image inspect hafigo/expose

docker container create --name expose -p 8080:8080 hafigo/expose

docker container start expose

docker container ls

docker container stop expose

# ENV Instruction
docker build -t hafigo/env env

docker image inspect hafigo/env

docker container create --name env --env APP_PORT=9090 -p 9090:9090 hafigo/env

docker container start env

docker container ls

docker container logs env

docker container stop env

# VOLUME Instruction
docker build -t hafigo/volume volume

docker image inspect hafigo/volume

docker container create --name volume -p 8080:8080 hafigo/volume

docker container start volume

docker container logs volume

docker container inspect volume

#15a53c9a60b9aaddb3c294cde03e6f283f319acf0db3e40c5d4b4a992a6451f1

docker volume ls

# WORKDIR Instruction
docker build -t hafigo/workdir workdir

docker container create --name workdir -p 8080:8080 hafigo/workdir

docker container start workdir

docker container exec -i -t workdir /bin/sh

# USER Instruction
docker build -t hafigo/user user

docker container create --name user -p 8080:8080 hafigo/user

docker container start user

docker container exec -i -t user /bin/sh

# ARG Instruction
docker build -t hafigo/arg arg --build-arg app=ngoding

docker container create --name arg -p 8080:8080 hafigo/arg

docker container start arg

docker container exec -i -t arg /bin/sh

# HEALTHCHECK Instruction
docker build -t hafigo/health health

docker container create --name health -p 8080:8080 hafigo/health

docker container start health

docker container ls

docker container inspect health

# ENTRYPOINT Instruction
docker build -t hafigo/entrypoint entrypoint

docker image inspect hafigo/entrypoint

docker container create --name entrypoint -p 8080:8080 hafigo/entrypoint

docker container start entrypoint

# Multi Stage Build
docker build -t hafigo/multi multi

docker image ls

docker container create --name multi -p 8080:8080 hafigo/multi

docker container start multi

# Docker Push
docker tag hafigo/multi registry.digitalocean.com/programmerzamannow/multi

docker --config /Users/hafigo/.docker-digital-ocean/ push registry.digitalocean.com/programmerzamannow/multi

docker --config /Users/hafigo/.docker-digital-ocean/ pull registry.digitalocean.com/programmerzamannow/multi