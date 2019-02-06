# build stage
FROM node:10-alpine as build-stage

RUN apk add --no-cache bash git openssh

RUN git clone https://github.com/favhub/client.git /app/

WORKDIR /app

RUN npm i

RUN npm run build

# production stage
FROM nginx:1.13.12-alpine as production-stage

COPY nginx/nginx.conf /etc/nginx/nginx.conf
COPY nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=build-stage /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
