FROM nfcore/base:1.12.1

LABEL author="Charlotte West" \
      description="Docker image containing all software requirements for the distiller-nf HiC mapping pipeline"

# Install the conda environment
COPY environment.yml /
RUN conda env create --quiet -f /environment.yml && conda clean -a

# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/distiller-env/bin:$PATH

# Dump the details of the installed packages to a file for posterity
RUN conda env export --name distiller-env > distiller-env.yml

# ----- OLD DOCKERFILE ----- #
# FROM ubuntu:16.04

# RUN apt-get update --fix-missing && \
#   apt-get install -q -y wget curl bzip2 libbz2-dev git build-essential zlib1g-dev locales vim fontconfig ttf-dejavu

# # Set the locale
# RUN locale-gen en_US.UTF-8  
# ENV LANG en_US.UTF-8  
# ENV LANGUAGE en_US:en  
# ENV LC_ALL en_US.UTF-8     

# # Install conda
# RUN curl -LO http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh && \
#     bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda3 -b && \
#     rm Miniconda3-latest-Linux-x86_64.sh 
# ENV PATH=/miniconda3/bin:${PATH}

# # Install conda dependencies
# ADD environment.yml /
# ADD VERSION /
# RUN pwd
# RUN conda config --set always_yes yes --set changeps1 no && \
#     conda config --add channels conda-forge && \
#     conda config --add channels defaults && \
#     conda config --add channels bioconda && \
#     conda config --add channels golobor && \ 
#     conda config --get && \
#     conda update -q conda && \
#     conda info -a && \
#     conda env update -q -n root --file environment.yml && \
#     conda clean --tarballs --index-cache --lock

