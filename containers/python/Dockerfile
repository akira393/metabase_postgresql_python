FROM python:3.8

RUN apt-get update -y \
    && apt-get upgrade -y

RUN curl -sL https://deb.nodesource.com/setup_12.x |bash - \
    && apt-get install -y --no-install-recommends \
    wget \
    git \
    curl \
    make \
    cmake \
    nodejs \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -rf \
        /var/lib/apt/lists/* \
        /var/cache/apt/* \
        /usr/local/src/* \
        /tmp/*

# install jupyterlab & extentions
RUN pip3 install --upgrade --no-cache-dir \
    'jupyterlab' \
    jupyterlab_code_formatter \
    yapf \
    && rm -rf ~/.cache/pip \
    && jupyter labextension install \
        @hokyjack/jupyterlab-monokai-plus \
        @ryantam626/jupyterlab_code_formatter \
    && jupyter serverextension enable --py jupyterlab_code_formatter

# install python library
RUN pip3 install --no-cache-dir pandas \
    sqlalchemy \
    psycopg2 \
    && rm -rf ~/.cache/pip


WORKDIR /home/work/