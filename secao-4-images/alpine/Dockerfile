# DEFINE ARGUMENTOS QUE PODEM SER ENCAMINHADOS NO BUILD DA IMAGEM
ARG ALPINE_VERSION=3.21.7

# FROM alpine:3.23.5
FROM alpine:${ALPINE_VERSION}

ENV MSG="Variável de ambiente criada no Dockerfile"

# INSTALANDO DEPENDENCIAS NO SO
RUN apk add --no-cache nodejs
RUN apk add --no-cache npm
RUN apk add --no-cache git
RUN apk add --no-cache nano
RUN echo ${MSG} > /tmp/arquivo_criado_durante_o_build_da_imagem.txt

# Outros maneiras de escrever (mas que são usadados para instalação de dependências no SO)
# RUN apk add --no-cache nodejs && apk add --no-cache npm && apk add --no-cache git

# RUN apk add --no-cache nodejs && \
#    apk add --no-cache npm && \
#    apk add --no-cache git

# RUN apk add --no-cache nodejs \
#    && apk add --no-cache npm \
#    && apk add --no-cache git

# RUN <<EOF
#    apk add --no-cache nodejs
#    apk add --no-cache npm
#    apk add --no-cache git
# EOF

ENV DESENVOLVEDOR="Vinícius Goncalves"  

# ADIÇÃO DE RÓTULOS(METADADOS) PARA A IMAGEM
LABEL desenvolvedor=${DESENVOLVEDOR}
LABEL descricao="Imagem baseada no Alpine Linux com Node.js, npm e git instalados"
LABEL versao="1.0"
LABEL contato="+55 11 99999-9999"

# Outros maneiras de escrever
# LABEL desenvolvedor="Vinicius Gonçalves" descricao="Imagem baseada no Alpine Linux com Node.js, npm e git instalados" versao="1.0" contato="+55 11 99999-9999"

# LABEL desenvolvedor=${DESENVOLVEDOR} \
#      descricao="Imagem baseada no Alpine Linux com Node.js, npm e git instalados" \
#      versao="1.0" \
#      contato="+55 11 99999-9999"

ARG FRONT_PRD="https://www.meuapp.com.br"
ARG BACK_PRD="https://meuapp.com.br:8080"

# VARIÁVEIS DE AMBIENTE
ENV FRONT_PRD=${FRONT_PRD}
ENV BACK_PRD=${BACK_PRD}

# Outras maneiras de escrever 
#ENV VERSAO_APP "1.0.0"

#ENV FRONT_PRD="https://www.meuapp.com.br" \
#    BACK_PRD="https://meuapp.com.br:8080" \
#    VERSAO_APP="1.0.0"