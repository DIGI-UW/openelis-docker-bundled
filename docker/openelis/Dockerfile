# Start from the official OpenELIS image
FROM itechuw/openelis-global-2:latest

# ---------------------------
# Embed only volume files
# ---------------------------

# Plugins
COPY ./volumes/plugins /var/lib/openelis-global/plugins

# System properties
COPY ./volumes/properties/SystemConfiguration.properties /var/lib/openelis-global/properties/SystemConfiguration.properties

# OCL files
COPY ./volumes/ocl /var/lib/openelis-global/ocl

# Test mappings
COPY ./volumes/test-map/test-loinc-map.csv /var/lib/openelis-global/plugin-test-mappings/test-loinc-map.csv
COPY ./volumes/odoo/odoo-test-product-mapping.csv /var/lib/openelis-global/odoo/odoo-test-product-mapping.csv


# ---------------------------
# Embed secrets (simulate Docker secrets)
# ---------------------------
USER root
# Create secrets directory
RUN mkdir -p /run/secrets \
    && chown -R tomcat_admin:tomcat /run/secrets \
    && chmod 600 /run/secrets/*

# Copy secrets into /run/secrets
COPY ./volumes/properties/datasource.password /run/secrets/datasource.password
COPY ./volumes/properties/common.properties /run/secrets/common.properties

# Create empty directories for logs and Lucene index (writable)
RUN mkdir -p /var/lib/openelis-global/logs /usr/local/tomcat/logs /var/lib/lucene_index \
    && chown -R tomcat_admin:tomcat /var/lib/openelis-global/logs /usr/local/tomcat/logs /var/lib/lucene_index \
    && chmod -R 770 /var/lib/openelis-global/logs /usr/local/tomcat/logs /var/lib/lucene_index

# ---------------------------
# Final runtime settings
# ---------------------------

# Set user
USER tomcat_admin

# Expose ports
EXPOSE 8080 8443

# Set entrypoint
ENTRYPOINT [ "/docker-entrypoint.sh" ]