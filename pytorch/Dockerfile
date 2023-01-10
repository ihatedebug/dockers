# TODO: find version from nvidia matrix pytorch:xx.xx
FROM nvcr.io/nvidia/pytorch:19.08-py3
    #RUN apt-get update
    #RUN apt-get dist-upgrade -y
   # Run apt-get install -y dialog
    # it will prevent dialog~~ error
    ENV DEBIAN_FRONTEND noninteractive
    RUN apt-get update && apt-get install -y --no-install-recommends apt-utils

    # support ssh connection
    RUN apt-get install -y openssh-server
    RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config

    # using zsh
    RUN apt-get install -y zsh && chsh -s `which zsh`
    RUN sh -c "$(wget <https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh> -O -)"

    # using custom env set
    RUN git clone https://github.com/TPFRL/envset.git
    WORKDIR envset
    RUN chmod +x envset.sh
    RUN zsh envset.sh

    # starting ssh with docker start. can change zsh to bash if you don't use zsh
    ENTRYPOINT service ssh start && zsh
    ENV DEBIAN_FRONTEND teletype
~
