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

ENTRYPOINT ["/bin/sh", "-c", "\
    if [ -d '/etc/nginx/certs' ]; then chown -R nginx:nginx /etc/nginx/certs || true; chmod 644 /etc/nginx/certs/* || true; fi; \
    if [ -d '/etc/nginx/keys' ]; then chown -R nginx:nginx /etc/nginx/keys || true; chmod 600 /etc/nginx/keys/* || true; fi; \
    exec nginx -g 'daemon off;' \
"]
