FROM node:lts-alpine as builder
LABEL authors="Undervis, Thinker90"

WORKDIR /app
COPY . .

RUN npm install && npm run build

FROM nginx:alpine

WORKDIR /usr/share/nginx/html
RUN rm -rf ./*

WORKDIR /

COPY --from=builder /app/nginx/default.conf /etc/nginx/conf.d
COPY --from=builder /app/dist /usr/share/nginx/html


ENTRYPOINT ["nginx", "-g", "daemon off;"]