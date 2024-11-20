FROM debian:latest

RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y \
    telnetd \
    samba \
    mc \
    vim \
    neofetch \
    curl \
    xinetd \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash s-o && \
    echo 's-o:password' | chpasswd

RUN echo -e "service telnet {\n\
    disable = no\n\
    socket_type = stream\n\
    protocol = tcp\n\
    wait = no\n\
    user = root\n\
    server = /usr/sbin/in.telnetd\n\
    log_on_failure += USERID\n\
}" > /etc/xinetd.d/telnet

EXPOSE 23 139 445

CMD ["/bin/bash"]
