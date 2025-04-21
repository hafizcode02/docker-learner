FROM golang:1.18-alpine

RUN apk add --no-cache git
WORKDIR /app

COPY main.go .

EXPOSE 8080
ENTRYPOINT ["go", "run"]
CMD ["main.go"]
