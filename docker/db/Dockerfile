# Use the official PostgreSQL 14.4 image as base
FROM postgres:14.4

RUN apt-get update && apt-get install -y gettext-base && rm -rf /var/lib/apt/lists/*
# Copy initialization scripts and data files into the container
# PostgreSQL will automatically run any *.sql or *.sh files in this folder
COPY ./volumes/database/dbInit /docker-entrypoint-initdb.d

RUN chmod 644 /docker-entrypoint-initdb.d/*.sql \
    && chmod 755 /docker-entrypoint-initdb.d/*.sh

# Optional: Set working directory (not strictly needed)
WORKDIR /docker-entrypoint-initdb.d

# Expose the PostgreSQL port
EXPOSE 5432