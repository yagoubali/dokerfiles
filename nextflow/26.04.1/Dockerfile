# Use an official OpenJDK base image as Nextflow requires Java 11 or later
FROM openjdk:17-slim

# Maintainer metadata
LABEL maintainer="Yagoub Adam"
LABEL description="Docker image for Nextflow version 26.04.1, a workflow management system for bioinformatics and data science pipelines."
Label version="26.04.1"

# Install necessary system dependencies (curl and bash)
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    curl \
    bash \
    && rm -rf /var/lib/apt/lists/*

# Set up the working directory for Nextflow installation
WORKDIR /usr/local/bin

# Download the specific Nextflow binary version, make it executable, and initialize it
RUN curl -Ls -o nextflow https://github.com/nextflow-io/nextflow/releases/download/v26.04.1/nextflow && \
    chmod +x nextflow && \
    ./nextflow -version

# Set the working directory for data processing tasks
WORKDIR /data

# Define the default command to show Nextflow help
CMD ["nextflow", "-help"]
