# build frontend from source
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY . .

RUN npm install; \
    npm run build


# create runtime image
FROM caddy:alpine

COPY ./caddy/Caddyfile /etc/caddy/Caddyfile
COPY --from=build /usr/src/app/build /usr/share/caddy

EXPOSE 8080
