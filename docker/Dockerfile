FROM node:22-alpine AS builder-front

WORKDIR /app

COPY ./front/package.json .

RUN npm install

COPY ./front .

FROM node:22-alpine

WORKDIR /app

COPY ./back/package.json .

RUN npm install

COPY ./back .

EXPOSE 5173
EXPOSE 3000

ENV ADDRESS=0.0.0.0 PORT=5173

COPY --from=builder-front /app /app/front

CMD ["npm", "start", "--prefix", "/app/front"]


# FROM nginx:1.27-alpine

# WORKDIR /root/

# COPY ./docker/nginx.conf /etc/nginx/nginx.conf
# COPY --from=builder-front /app/dist /usr/share/nginx/html

# EXPOSE 80

# CMD ["nginx", "-g", "daemon off;"]
