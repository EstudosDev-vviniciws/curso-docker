# Estágio 0
FROM ubuntu AS build

RUN apt update && apt install build-essential -y 

RUN mkdir /opt/app

WORKDIR /opt/app

COPY Main.c .
# /opt/app/Main.c

RUN gcc ./Main.c -static -o Main

# Estágio 1
FROM alpine AS prd

COPY --from=build /opt/app/Main /opt/app/Main

# Estágio 2
FROM prd AS run

CMD ["/opt/app/Main"]

