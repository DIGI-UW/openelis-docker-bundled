# Use the existing OpenELIS FHIR image as base
FROM itechuw/openelis-global-2-fhir:3.2.0.2

# Switch to root to copy the YAML
USER root

# Ensure the target directory exists
RUN mkdir -p /opt/openelis/config

# Copy your HAPI application YAML into the image
COPY ./volumes/properties/hapi_application.yaml /opt/openelis/config/hapi_application.yaml

# Ensure proper permissions so tomcat can read it
RUN chown tomcat_admin:tomcat /opt/openelis/config/hapi_application.yaml \
    && chmod 600 /opt/openelis/config/hapi_application.yaml

# Optionally, set SPRING_CONFIG_LOCATION so the container automatically picks it up
ENV SPRING_CONFIG_LOCATION=file:///opt/openelis/config/hapi_application.yaml

# Switch back to tomcat user
USER tomcat_admin