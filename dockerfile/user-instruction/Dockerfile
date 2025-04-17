FROM golang:1.18-alpine

RUN mkdir /app

# Add a non-root user to run the application (safety purpose)
RUN addgroup -S hafigogroup
RUN adduser -S -D -h /app hafigouser hafigogroup
RUN chown -R hafigouser:hafigogroup /app

USER hafigouser

COPY main.go /app

EXPOSE 8080
CMD go run /app/main.go