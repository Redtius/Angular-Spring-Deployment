# Stage 3: MySQL Database
FROM mysql:latest

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=employee_management_system

# Copy the SQL initialization script to the container
COPY init.sql /docker-entrypoint-initdb.d/

# Expose port 3306
EXPOSE 3306