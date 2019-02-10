FROM node:10-alpine

RUN apk add --no-cache bash git openssh python make g++

RUN git clone https://github.com/favoriteshub/api.git /api/

WORKDIR /api

RUN npm i --production

EXPOSE 3000

CMD ["npm", "start"]