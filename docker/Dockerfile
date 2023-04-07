FROM ubuntu:22.04

RUN set -x && \
    apt update -y && \
    apt install -y \
        curl \
        gcc \
        pkg-config \
        ca-certificates \
        git && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

RUN set -x && \
    apt update -y && \
    apt install -y \
        libssl-dev \
        libsqlite3-dev && \
    apt-get autoremove -y && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/mr-abramenko/raf.git

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y

RUN <<EOT bash -e
    cd raf
    source ~/.cargo/env
    cargo install --path .
EOT

ENV BOT_NAME=""  
ENV TOKEN=""

CMD [ "/raf/target/release/raf" ]
