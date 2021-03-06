FROM ubuntu:20.04

RUN apt update 
RUN apt install --assume-yes --fix-broken \
    curl \
    git \
    gnupg \
    htop \
    locales \    
    python3 \
    python3-pip \
    sudo \
    tig \
    unzip \
    vim \
    wget \
    zsh

RUN locale-gen en_US.UTF-8

RUN chmod a+rx /root

RUN bash -c "$(curl -fsSL https://raw.githubusercontent.com/mihaigalos/utils/master/setmeup/setup_oh_my_zsh.sh)"
RUN bash -c "$(curl -fsSL https://raw.githubusercontent.com/mihaigalos/utils/master/setmeup/setup_vim.sh)"

RUN wget https://raw.githubusercontent.com/mihaigalos/utils/master/url-install/url-install.sh
RUN chmod a+x url-install.sh
RUN mv url-install.sh /usr/bin/url-install

RUN url-install \
    https://github.com/sharkdp/bat/releases/download/v0.16.0/bat-v0.16.0-x86_64-unknown-linux-gnu.tar.gz \
    https://github.com/dandavison/delta/releases/download/0.4.4/delta-0.4.4-x86_64-unknown-linux-gnu.tar.gz \
    https://github.com/Byron/dua-cli/releases/download/v2.10.2/dua-v2.10.2-x86_64-unknown-linux-musl.tar.gz \
    https://github.com/ogham/exa/releases/download/v0.9.0/exa-linux-x86_64-0.9.0.zip \
    https://github.com/XAMPPRocky/tokei/releases/download/v12.0.4/tokei-x86_64-unknown-linux-gnu.tar.gz \
    https://github.com/beefsack/webify/releases/download/v1.5.0/webify-v1.5.0-linux-amd64.tar.gz

COPY .gitconfig /root

RUN cp /root/.zshrc /etc/zsh/zshrc
RUN echo '[ ! -f "/home/$USER/.gitconfig" ] && ln -s /root/.gitconfig /home/$USER/' >> /etc/zsh/zshrc

CMD /bin/zsh

