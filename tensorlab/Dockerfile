FROM nvidia/cuda
MAINTAINER Devin Conathan

# conda version
ENV CONDA_VERSION 4.3.21

# env variables
ENV CONDA_DIR /opt/conda

# install conda
RUN apt-get update && \
    apt-get install -y wget && \
    wget http://repo.continuum.io/miniconda/Miniconda3-${CONDA_VERSION}-Linux-x86_64.sh -O /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -b -p $CONDA_DIR && \
    rm -rf /var/lib/apt/lists/*

# install packages
ENV PATH $CONDA_DIR/bin:$PATH
RUN mkdir /lab && \
    conda install -y -c conda-forge jupyter \
                                    jupyterlab \ 
                                    tensorflow-gpu

WORKDIR /lab
EXPOSE 8888

ENTRYPOINT ["jupyter-lab"]
CMD ["--ip=0.0.0.0", "--allow-root", "--no-browser", "--notebook-dir=/lab"]
