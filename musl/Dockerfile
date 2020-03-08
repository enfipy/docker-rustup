FROM liuchong/rustup:1.41.1-musl AS builder

ENV RUSTFLAGS=-Clinker=musl-gcc
RUN apt-get -y remove openssl \
    && DEBIAN_FRONTEND=noninteractive apt-get -q update \
    && apt-get -qy install wget make gcc clang llvm-dev libclang-dev
RUN wget https://www.openssl.org/source/openssl-1.0.2g.tar.gz \
    && tar -xzvf openssl-1.0.2g.tar.gz \
    && cd openssl-1.0.2g \
    && ./config \
    && make install \
    && ln -sf /usr/local/ssl/bin/openssl 'which openssl'
RUN cargo install cargo-build-deps
