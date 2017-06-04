FROM ubuntu:17.04

ENV RUST_TARGET x86_64-unknown-linux-gnu
ENV RUST_DISTRIB rust-nightly-$RUST_TARGET
ENV DOCKER_VERSION 17.03.0-ce

WORKDIR /rust

RUN apt-get -y update && apt-get install -q -y \
    build-essential \
    curl \
    git-core \
    libssl-dev \
    openssh \
    && \

    curl -LO "https://static.rust-lang.org/dist/${RUST_DISTRIB}.tar.xz" && \
    tar xvJf "${RUST_DISTRIB}.tar.xz" && \
    "${RUST_DISTRIB}/install.sh" --components="rustc,cargo,rust-std-${RUST_TARGET}" && \
    rm -r /rust && \

    curl -L -o "/tmp/docker-${DOCKER_VERSION}.tgz" "https://get.docker.com/builds/Linux/x86_64/docker-${DOCKER_VERSION}.tgz" && \
    tar -xz -C /tmp -f "/tmp/docker-${DOCKER_VERSION}.tgz" && \
    mv /tmp/docker/* /usr/bin

WORKDIR /
