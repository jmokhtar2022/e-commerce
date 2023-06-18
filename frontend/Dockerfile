FROM node:16-alpine AS build
# Create a Virtual directory inside the docker image
WORKDIR /app/dist/shop
# Copy files to virtual directory
# COPY package.json package-lock.json ./
# Run command in Virtual directory
RUN npm cache clean --force
# Copy files from local machine to virtual directory in docker image
COPY . .
RUN npm install
RUN npm run build --prod


### STAGE 2:RUN ###
# Defining nginx image to be used
FROM nginx:latest AS ngi
# Copying compiled code and nginx config to different folder
# NOTE: This path may change according to your project's output folder 
COPY --from=build /app/dist/shop /usr/share/nginx/html
COPY /nginx.conf  /etc/nginx/conf.d/default.conf
