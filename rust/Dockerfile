FROM debian:9.5-slim

LABEL "com.github.actions.name"="Rust Semverver"
LABEL "com.github.actions.description"="Run semverver checks on PRs"
LABEL "com.github.actions.icon"="mic"
LABEL "com.github.actions.color"="purple"

LABEL "repository"="http://github.com/ryankurte/action-cargo-semver"
LABEL "homepage"="http://github.com/ryankurte/action-cargo-semves"
LABEL "maintainer"="Ryan <ryankurte@gmail.com>"

ENV PATH="/root/.cargo/bin:${PATH}"
RUN apt-get update \
    && apt-get install curl build-essential libssl-dev pkg-config -y \
    && rm -rf /var/lib/apt/lists/*

RUN curl https://sh.rustup.rs -sSf | sh -s -- --default-toolchain nightly -y

RUN export PATH="/root/.cargo/bin:${PATH}"

RUN rustup update nightly && cargo +nightly install semverver

ADD entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
