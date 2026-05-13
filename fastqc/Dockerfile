FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="FastQC 0.12.1 for raw and trimmed read QC"
LABEL version="0.12.1"

# Use micromamba to install FastQC
RUN apt-get update && apt-get install -y procps
RUN micromamba install -y -n base \
    -c bioconda \
    -c conda-forge \
    fastqc=0.12.1 \
    && micromamba clean --all --yes

# Activate base env by default
ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["fastqc", "--version"]
