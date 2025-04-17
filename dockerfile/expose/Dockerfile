FROM golang:1.18-alpine

RUN mkdir app
COPY main.go app

# Not Required Actually, just tells the container to listen on port 8080
EXPOSE 8080

CMD go run app/main.go