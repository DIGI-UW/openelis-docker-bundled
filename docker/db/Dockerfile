# Use the official PostgreSQL 14.4 image as base
FROM postgres:14.4

# Set environment variables for default DB, user, and password
# These will be used when the container is first initialized
ENV POSTGRES_DB=clinlims
ENV POSTGRES_USER=clinlims
ENV POSTGRES_PASSWORD=clinlims

# Copy initialization scripts and data files into the container
# PostgreSQL will automatically run any *.sql or *.sh files in this folder
COPY ./volumes/database/dbInit /docker-entrypoint-initdb.d

# Optional: Set working directory (not strictly needed)
WORKDIR /docker-entrypoint-initdb.d

# Expose the PostgreSQL port
EXPOSE 5432