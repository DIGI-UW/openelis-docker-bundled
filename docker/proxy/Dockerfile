FROM itechuw/openelis-global-2-proxy:3.2.0.2
USER root

COPY ./volumes/nginx/nginx.conf /etc/nginx/nginx.conf
EXPOSE 80 443

ENTRYPOINT ["nginx", "-g", "daemon off;"]