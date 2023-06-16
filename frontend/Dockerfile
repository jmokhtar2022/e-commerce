#stage 1
FROM node:latest as node
WORKDIR /app
COPY . .
ENV NODE_OPTIONS="--openssl-legacy-provider"
RUN npm install
RUN npm run build --prod
#stage 2
FROM nginx:alpine
COPY --from=node /app/dist/shop /usr/share/nginx/html