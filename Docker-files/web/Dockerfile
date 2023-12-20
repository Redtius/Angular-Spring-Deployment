# Stage 1: Build the Angular app
FROM node:12.11.1 AS builder

WORKDIR /app

COPY . .

RUN npm install
RUN npm run build --prod

# Stage 2: Use Nginx to serve the built Angular app
FROM nginx:latest

# Copy the built Angular app from the builder stage
COPY --from=builder /app/dist /usr/share/nginx/html

# Copy Nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]