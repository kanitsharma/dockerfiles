FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive 

ARG USERNAME=kanitsharma

# SETUP USER
RUN apt update && \
    apt install -y sudo fish && \
    adduser --quiet --disabled-password --shell /usr/bin/fish --home /home/${USERNAME} --gecos "User" ${USERNAME}

# INSTALL DEV PACKAGES
RUN apt update && \
    apt install -y curl git-core  && \
    sh -c "$(curl -fsSL https://starship.rs/install.sh)" -- --yes

USER kanitsharma
SHELL ["fish", "--command"]
ENV LANG=C.UTF-8 LANGUAGE=C.UTF-8 LC_ALL=C.UTF-8

RUN echo "starship init fish | source" > $HOME/.config/fish/config.fish
ENTRYPOINT [ "fish" ]