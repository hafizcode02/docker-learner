
FROM golang:1.18-alpine

RUN mkdir /app/
COPY main.go /app/

EXPOSE 8080

# entrypoint.sh is like a script that runs when the container starts, eg : npm start, python app.py
# ENTRYPOINT ["sh", "/app/entrypoint.sh"]
# ENTRYPOINT ["sh", "-c", "cd /app && go run main.go"]
# ENTRYPOINT ["executable", "arg1", "arg2"]
ENTRYPOINT ["go", "run"]

# While using ENTRYPOINT, CMD is used to provide default arguments to the ENTRYPOINT command.
CMD ["/app/main.go"]