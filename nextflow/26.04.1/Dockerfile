# Use an official OpenJDK base image as Nextflow requires Java 11 or later
FROM ubuntu:22.04

# Prevent interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Maintainer metadata
LABEL maintainer="Yagoub Adam"
LABEL description="Docker image for Nextflow version 26.04.1, a workflow management system for bioinformatics and data science pipelines."
Label version="26.04.1"

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    graphviz \
    openjdk-17-jre-headless \
    python3 \
    gpg \
    ca-certificates \
    libsquashfs-dev \
    libseccomp-dev \
    pkg-config \
    squashfs-tools \
    cryptsetup \
    libssl-dev \
    uuid-dev \
    libgpgme11-dev \
    squashfs-tools \
    libseccomp-dev \
    gnupg \
    bash \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN install -m 0755 -d /etc/apt/keyrings \
    && curl -fsSL https://docker.com | gpg --dearmor -o /etc/apt/keyrings/docker.gpg \
    && chmod a+r /etc/apt/keyrings/docker.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://docker.com $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
    tee /etc/apt/sources.list.d/docker.list > /dev/null \
    && apt-get update && apt-get install -y docker-ce-cli

    # Note: Apptainer is the open-source successor to Singularity
RUN apt-get update && apt-get install -y software-properties-common \
    && add-apt-repository -y ppa:apptainer/ppa \
    && apt-get update && apt-get install -y apptainer

RUN wget -qO - https://sylabs.io | sudo gpg --dearmor -o /usr/share/keyrings/sylabs-archive-keyring.gpg  && \
        echo "deb [signed-by=/usr/share/keyrings/sylabs-archive-keyring.gpg] https://sylabs.io $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/sylabs.list && \
        apt-get update  && apt-get install -y singularity-ce &&
        apt-get install -y apptainer

# Install necessary system dependencies (curl and bash)
# RUN apt-get update && \
#     apt-get install -y --no-install-recommends \
#     curl \
#     bash \
#     openjdk-17-jre-headless \
#     && rm -rf /var/lib/apt/lists/*

# Set up the working directory for Nextflow installation
WORKDIR /usr/local/bin

# Download the specific Nextflow binary version, make it executable, and initialize it
RUN curl -Ls -o nextflow https://github.com/nextflow-io/nextflow/releases/download/v26.04.1/nextflow && \
    chmod +x nextflow && \
    nextflow -version && \
    mkdir -p /data  && \
    chmod -R 777 /data


# Set the working directory for data processing tasks
WORKDIR /data

# Define the default command to show Nextflow help
CMD ["nextflow", "-help"]
