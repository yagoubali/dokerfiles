FROM mambaorg/micromamba:1.5.8

LABEL maintainer="yagoub.adam@fiocruz.br"
LABEL description="SeqKit 2.13.0 for FASTA/FASTQ manipulation"
LABEL version="2.13.0"

# Note: the original config uses 'bioconda::seqkit:2.13.0' (colon separator)
# which is a typo — correct conda syntax uses '=' as the version separator.
RUN micromamba install -y -n base \
    -c bioconda \
    -c conda-forge \
    seqkit=2.13.0 \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
ARG MAMBA_DOCKERFILE_ACTIVATE=1

WORKDIR /data

CMD ["seqkit", "version"]
