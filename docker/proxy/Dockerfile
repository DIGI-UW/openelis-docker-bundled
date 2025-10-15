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

# Fix permissions
RUN chown -R nginx:nginx /etc/nginx/certs /etc/nginx/keys && \
    chmod -R 600 /etc/nginx/certs /etc/nginx/keys && \
    chown nginx:nginx /etc/nginx/nginx.conf && \
    chmod 644 /etc/nginx/nginx.conf

# Switch back to the nginx user (as in the base image)
USER nginx

# ---------------------------
# Expose ports
# ---------------------------
EXPOSE 80 443
