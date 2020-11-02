FROM rust:1.47.0-buster

ARG USERNAME=app
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ENV SHELL=/bin/bash

RUN groupadd --gid $USER_GID $USERNAME \
  && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
  && curl -sL https://deb.nodesource.com/setup_14.x | bash - \
  && apt-get update \
  && apt-get install -y sudo \
  && echo "$USERNAME ALL=(root) NOPASSWD:ALL" > /etc/sudoers.d/$USERNAME \
  && chmod 0440 /etc/sudoers.d/$USERNAME

RUN mkdir -p /app
RUN chown -R $USERNAME /app

USER $USERNAME

WORKDIR /app
