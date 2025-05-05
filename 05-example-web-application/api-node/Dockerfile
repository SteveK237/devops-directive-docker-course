# test build
FROM node:19.6-alpine

RUN apt update && apt install nodejs npm -y

COPY . .

RUN npm install

CMD [ "npm", "run", "dev" ]
