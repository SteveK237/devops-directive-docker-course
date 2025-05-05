# test build
FROM node

WORKDIR /usr/src/docker

ENV NODE_ENV=production

RUN apt update && apt install nodejs npm -y

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/docker/.npm \
  npm set cache /usr/src/docker/.npm && \
  npm ci --only=production

USER node

COPY --chown=node:node ./src .

EXPOSE 3000

CMD [ "node", "index.js" ]
