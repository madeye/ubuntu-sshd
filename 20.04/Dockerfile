FROM       ubuntu:20.04
MAINTAINER Aleksandar Diklic "https://github.com/rastasheep"

RUN apt-get update

ENV DEBIAN_FRONTEND="noninteractive" TZ="Asia/Shanghai"

RUN apt-get install -y openssh-server cmake build-essential vim git git-lfs locales

RUN sed -i '/en_US.UTF-8/s/^# //g' /etc/locale.gen && \
            locale-gen

RUN mkdir /var/run/sshd

RUN echo 'root:root' |chpasswd

RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN mkdir /root/.ssh

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 22

CMD    ["/usr/sbin/sshd", "-D"]
