FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive 

ARG USERNAME=kanitsharma

# SETUP USER
RUN apt update && \
    apt install -y sudo && \
    adduser --quiet --disabled-password --shell /bin/bash --home /home/${USERNAME} --gecos "User" ${USERNAME} && \
    echo ${USERNAME} ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/${USERNAME} && \
    chmod 0440 /etc/sudoers.d/${USERNAME}

# INSTALL FISH AND STARSHIP-PROMPT
RUN apt install -y curl git-core fish  && \
    sh -c "$(curl -fsSL https://starship.rs/install.sh)" -- --yes

USER ${USERNAME}
SHELL ["fish", "--command"]
ENV LANG=C.UTF-8 LANGUAGE=C.UTF-8 LC_ALL=C.UTF-8

RUN echo "starship init fish | source" > $HOME/.config/fish/config.fish
ENTRYPOINT [ "fish" ]