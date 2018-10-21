FROM ubuntu:16.04
LABEL maintainer="kenny.lee28@gmail.com"

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    && echo "deb http://ppa.launchpad.net/inkscape.dev/stable/ubuntu xenial main" >> /etc/apt/sources.list \ 
    && echo "deb-src http://ppa.launchpad.net/inkscape.dev/stable/ubuntu xenial main " >> /etc/apt/sources.list \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-key 22C4850146603F3DB0ED00479DA4BD18B9A06DE3 \
    && apt-get update && apt-get install -y \
    inkscape \
    && rm -rf /var/lib/apt/lists/*

ENV HOME /home/inkscape
RUN useradd --create-home --home-dir $HOME inkscape \
    && chown -R inkscape:inkscape $HOME

WORKDIR $HOME
USER inkscape

CMD ["inkscape"]