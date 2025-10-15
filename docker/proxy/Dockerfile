# Use the existing OpenELIS Nginx proxy image as base
FROM itechuw/openelis-global-2-proxy:latest

# ---------------------------
# Switch to root to copy files
# ---------------------------
USER root

# ---------------------------
# Embed configuration and SSL files
# ---------------------------
COPY ./volumes/nginx/nginx.conf /etc/nginx/nginx.conf

# Switch back to the nginx user (as in the base image)
USER nginx

# ---------------------------
# Expose ports
# ---------------------------
EXPOSE 80 443
