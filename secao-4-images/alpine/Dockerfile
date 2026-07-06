# DEFINE ARGUMENTOS QUE PODEM SER ENCAMINHADOS NO BUILD DA IMAGEM
ARG ALPINE_VERSION=3.21.7

# FROM alpine:3.23.5
FROM alpine:${ALPINE_VERSION}

# DEFINE O DIRETÓRIO DE TRABALHO PARA OS PRÓXIMOS COMANDOS
WORKDIR /

RUN mkdir ./logs/

RUN echo "1 -Diretório de trabalho atual : $(pwd)" > /logs/1.txt

ENV MSG="Variável de ambiente criada no Dockerfile"

# INSTALANDO DEPENDENCIAS NO SO
RUN apk add --no-cache nodejs
RUN apk add --no-cache npm
RUN apk add --no-cache git
RUN apk add --no-cache nano
RUN apk add --no-cache unzip
# Adiciona um usuário no SO (Linux distro Alpine)
# RUN adduser -D Vinicius \
# Adiciona um grupo no SO (Linux distro Alpine)
#    && addgroup dev \
# Adiciona o usuário Vinicius ao grupo dev
#    && addgroup Vinicius dev
# DEFINE O USUÁRIO RESPONSÁVEL PELA EXECUÇÃO DOS PRÓXIMOS RUNs
# USER Vinicius
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

ENV DESCRICAO="Imagem baseada no Alpine Linux com Node.js, npm e git instalados"

# ADIÇÃO DE RÓTULOS(METADADOS) PARA A IMAGEM
LABEL desenvolvedor="Vinicius Gonçalves"
LABEL descricao=${DESCRICAO}
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
ENV BACK_PRD="https://meuapp.com.br:8000"

# Outras maneiras de escrever 
#ENV VERSAO_APP "1.0.0"

#ENV FRONT_PRD="https://www.meuapp.com.br" \
#    BACK_PRD="https://meuapp.com.br:8080" \
#    VERSAO_APP="1.0.0"

# PERMITE EFETUAR A COPIA DE ARQUIVOS DO HOST PARA O CONTAINER DURANTE O BUILD DA IMAGEM
ADD ./exemplo_1.txt /tmp/
COPY ./exemplo_1.txt /tmp/teste_copy/

# ADD ./exemplo_2.txt /tmp/
# COPY ./exemplo_2.txt /tmp/teste_copy/

# Efetua a cópia de arquivo e define o dono, grupo e permissões de leitura e escrita
# ADD --chown=Vinicius:dev --chmod=644 ./exemplo_3.txt /tmp/
# COPY --chown=Vinicius:dev --chmod=644 ./exemplo_3.txt /tmp/teste_copy/

# Outras maneiras de escrever
# ADD --chown=Vinicius:dev ./exemplo_* /tmp/curinga/
# COPY --chown=Vinicius:dev ./exemplo_* /tmp/copy_curinga/

# ADD --chown=Vinicius:dev ./exemplo_ab?.??? /tmp/curinga/

# ADD --chown=Vinicius:dev ./arquivos.zip /tmp/arquivos/
# COPY --chown=Vinicius:dev ./arquivos.zip /tmp/arquivos_copy/
# RUN cd /tmp/arquivos_copy \
#    && unzip arquivos.zip

# COPY ./exemplo_1.txt ./exemplo_2.txt ./exemplo_3.txt /tmp/copy_multi/

# COPY . /tmp/copy_all/

WORKDIR /opt/
RUN echo "2 -Diretório de trabalho atual : $(pwd)" > /logs/2.txt

ADD --chown=Vinicius:dev https://argus-academy.com/cursos/docker_-_dominando_a_criacao_e_o_gerenciamento_de_containers/server.tar.gz ./code/

WORKDIR /opt/code/
RUN echo "3 -Diretório de trabalho atual : $(pwd)" > /logs/3.txt

RUN tar -xvzf server.tar.gz \
    && rm -f server.tar.gz

# ADD --chown=Vinicius:dev https://argus-academy.com/cursos/docker_-_dominando_a_criacao_e_o_gerenciamento_de_containers/server.tar.gz /opt/app/
# RUN cd /opt/app/ \
#    && tar -xvzf server.tar.gz \
#    && rm -f server.tar.gz

# COMANDO EXECUTADO SOBRE A IMAGEM QUANDO O CONTAINER É INICIADO
# CMD ["echo", "Parâmetro 1 - Instrução via ENTRYPOINT"]
# ENTRYPOINT ["echo", "Parâmetro 1 - Instrução via ENTRYPOINT"]

# CMD ["/bin/sh", "-c", "node server.js"]
# CMD ["/bin/sh", "-c", "cd /opt/app/ && node server.js"]

# Combinando ENTRYPOINT e CMD
# ENTRYPOINT ["ls"]
# CMD ["-la"]

# COPY ./dockerfile-entrypoint.sh /start/dockerfile-entrypoint.sh
# ENTRYPOINT ["/start/dockerfile-entrypoint.sh"]

ENTRYPOINT ["node"]
CMD ["server.js"]

# DOCUMENTA QUAIS PORTAS DEVERÃO SER EXPOSTAS EM TEMPO DE EXECUÇÃO DO CONTAINER
# EXPOSE 3000
EXPOSE 3000/tcp
EXPOSE 3000/udp

EXPOSE 3030