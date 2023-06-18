# Stage 1: Build Angular app
FROM node:latest as node
WORKDIR /app
COPY . .
ENV NODE_OPTIONS="--openssl-legacy-provider"
RUN npm install
RUN npm run build --prod

# Stage 2: Serve Angular app with Nginx
FROM nginx:1.13.3-alpine
COPY /nginx/default.conf /etc/nginx/conf.d/
RUN rm -rf /usr/share/nginx/html/*
COPY --from=node /app/dist/shop /usr/share/nginx/html
