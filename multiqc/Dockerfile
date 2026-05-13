FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="MultiQC 1.21 for aggregating QC reports"
LABEL version="1.21"

# Use micromamba to install MultiQC
RUN apt-get update && apt-get install -y procps
RUN micromamba install -y -n base \
    -c bioconda \
    -c conda-forge \
    multiqc=1.21 \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["multiqc", "--version"]
