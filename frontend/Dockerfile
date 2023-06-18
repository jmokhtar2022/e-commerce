FROM node:16-alpine AS build
# Create a directory inside the docker image
WORKDIR /app

# Copy package.json and package-lock.json files to the image
COPY package.json package-lock.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the application
RUN npm run build --prod

# STAGE 2: Final NGINX stage
FROM nginx:latest

# Copy compiled code from the previous build stage
COPY --from=build /app/dist/shop /usr/share/nginx/html

# Copy nginx config file
COPY nginx/default.conf /etc/nginx/conf.d/default.conf