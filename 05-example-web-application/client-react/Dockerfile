FROM node:19.4-bullseye AS build

WORKDIR /usr/src/app

COPY package*.json ./

RUN --mount=type=cache,target=/usr/src/app/.npm \
  npm set cache /usr/src/app/.npm && \
  npm ci

COPY . .

RUN npm run build

## stage
FROM nginxinc/nginx-unprivileged:alpine3.21-perl

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build usr/src/app/dist/ /usr/share/nginx/html

# unpriv can't bind any port <1024
EXPOSE 8080
