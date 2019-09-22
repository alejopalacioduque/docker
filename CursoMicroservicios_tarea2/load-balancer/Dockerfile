FROM nginx:latest
# Copy the config file
COPY nginx.conf /etc/nginx/nginx.conf
# Copy the crt file
COPY ./cert/localhost.crt /etc/nginx/localhost.crt
# Copy the key file
COPY ./cert/localhost.key /etc/nginx/localhost.key

# Start Nginx when the container has provisioned.
CMD ["nginx", "-g", "daemon off;"]