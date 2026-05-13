FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="Python 3.11 environment for PARSE_FASTQC, EVALUATE_QC, REPORT, PARSE_DASHBOARD"
LABEL version="3.11"

# Use micromamba to install Python 3.11
RUN apt-get update && apt-get install -y procps

RUN micromamba install -y -n base \
    -c conda-forge \
    python=3.11 \
    pip \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["python", "--version"]
