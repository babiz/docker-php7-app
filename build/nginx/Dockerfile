# Base Image
FROM ubuntu:16.04

# Created By
MAINTAINER Babish Shrestha

# Install nginx in the ubuntu base image
RUN apt-get update \
    && apt-get install -y nginx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && echo "daemon off;" >> /etc/nginx/nginx.conf

# Copy the local nginx default
ADD default /etc/nginx/sites-available/default

# Expose port 80 for nginx
EXPOSE 80

# run the command to start nginx
CMD ["nginx"]
