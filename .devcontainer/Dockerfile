FROM haskell:9
# USER root

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    #
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME


RUN curl -L https://github.com/akinomyoga/ble.sh/releases/download/nightly/ble-nightly.tar.xz | tar xJf - -C /usr/local/share \
    && echo 'source /usr/local/share/ble-nightly/ble.sh' >> /home/$USERNAME/.bashrc  \
    && echo 'source /usr/local/share/ble-nightly/ble.sh' >> ~/.bashrc 

    
RUN curl -L https://github.com/lemonade-command/lemonade/releases/download/v1.1.1/lemonade_linux_amd64.tar.gz | tar xzf - -C /usr/local/bin \
    && echo "alias clip='lemonade --port=42489 copy'" >> /home/$USERNAME/.bashrc  \
    && echo "alias clip='lemonade --port=42489 copy'" >> ~/.bashrc  
    
