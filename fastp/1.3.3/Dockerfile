FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="fastp for adapter trimming and quality filtering"
LABEL version="1.3.3"

# Use micromamba to install fastp (latest from bioconda)
USER root
RUN apt-get update && apt-get install -y procps
USER $MAMBA_USER

RUN micromamba install -y -n base \
    -c bioconda \
    -c conda-forge \
    fastp=1.3.3 \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["fastp", "--version"]
