# Stage 1: Build the Go application
FROM golang:1.18-alpine as builder
WORKDIR /app/
COPY main.go /app/
RUN go build -o /app/main /app/main.go

# Stage 2: Create a minimal runtime image
FROM alpine:3
WORKDIR /app/
COPY --from=builder /app/main /app/
CMD /app/main