FROM ubuntu:17.04

ENV RUST_TARGET x86_64-unknown-linux-gnu
ENV RUST_DISTRIB rust-nightly-$RUST_TARGET

WORKDIR /rust
RUN apt-get -y update && apt-get install -q -y \
    build-essential \
    curl \
    libssl-dev && \
    curl -LO "https://static.rust-lang.org/dist/${RUST_DISTRIB}.tar.xz" && \
    tar xvJf "${RUST_DISTRIB}.tar.xz" && \
    "${RUST_DISTRIB}/install.sh" --components="rustc,cargo,rust-std-${RUST_TARGET}" && \
    rm -r /rust
WORKDIR /
