FROM ros:noetic

SHELL ["/bin/bash", "-c"]

RUN apt-get update && \
    apt-get install -y \
    build-essential \
    curl \
    libasound2-dev \
    libclang-dev \
    libfreetype6-dev \
    libglu1-mesa-dev \
    libudev-dev \
    xorg-dev \
    git-all

RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y

RUN source ~/.cargo/env && \
    cargo install cargo-tarpaulin && \
    # linter and formatter
    rustup component add clippy rustfmt && \
    # for VS Code Remote Container
    rustup component add rust-analysis rust-src rls

RUN git clone  --depth 1 https://github.com/openrr/openrr.git /root/openrr

WORKDIR /root/openrr

CMD [ "source", "/opt/ros/noetic/setup.bash", "&&", "git fetch"]