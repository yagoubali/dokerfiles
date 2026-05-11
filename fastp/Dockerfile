FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="fastp for adapter trimming and quality filtering"

# Use micromamba to install fastp (latest from bioconda)
RUN micromamba install -y -n base \
    -c bioconda \
    -c conda-forge \
    fastp \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["fastp", "--version"]
