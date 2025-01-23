# Use an Nginx base image
FROM nginx:alpine

# Set a working  directory
WORKDIR  /usr/share/nginx/html

#Copy the files
COPY . . 

# Expose port 80
EXPOSE 80


CMD ["nginx" , "-g" , "daemon off;"]
