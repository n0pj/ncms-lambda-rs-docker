# https://github.com/lambci/docker-lambda#documentation
FROM lambci/lambda:build-provided.al2

ARG USER_ID
ARG RUST_VERSION=1.57.0

RUN yum install -y jq openssl-devel
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs \
| CARGO_HOME=/cargo RUSTUP_HOME=/rustup sh -s -- -y --profile minimal --default-toolchain $RUST_VERSION

# ユーザーを作成
# ARG USER_ID=1000
RUN useradd -m -u ${USER_ID} docker

# 作成したユーザーに切り替える
USER ${USER_ID}

RUN cargo install cargo-watch
# RUN apt-get -y update
WORKDIR /code
