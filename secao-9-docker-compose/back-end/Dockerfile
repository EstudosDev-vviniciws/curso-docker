ARG NODE_VERSION=24.13.0-slim

FROM node:${NODE_VERSION} AS dev

WORKDIR /app

EXPOSE 3000

CMD /bin/sh -c "npm i && npm run start:dev"