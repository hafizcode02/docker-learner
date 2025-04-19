
FROM golang:1.18-alpine

# ARGUMENTS LIKE ENV but Used during image build time only (not available in the running container).
ARG app=main

RUN mkdir app
COPY main.go app

# it works its build time (use arg)
RUN mv app/main.go app/${app}.go 

EXPOSE 8080

ENV app=${app}

# it does't work because arguments is not avaliable in run time if you use ARG and not pass it to ENV
CMD go run app/${app}.go