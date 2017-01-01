# Run f.lux in a container
#
# docker run -d \
# 	     -v /tmp/.X11-unix/:/tmp/.X11-unix/ \
#	     -e DISPLAY=unix$DISPLAY \
#	     --name flux \
#	     kleesc/flux \
#	     xflux \
#	     -l <latitude> \
#	     -g <longitude> \
#	     -k <colortemp> \
#	     -nofork
#
FROM ubuntu:latest
MAINTAINER Kenny Lee Sin Cheong <kenny.lee28@gmail.com>

RUN apt-get update && apt-get install -y \
    dirmngr \
    gnupg \
    wget \
    ca-certificates \
    # dbus \
    # dbus-x11 \
    # libcanberra-gtk-module \
    libxxf86vm1 \
    --no-install-recommends \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 29A4B41A \
    && echo "deb http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu xenial main" >> /etc/apt/sources.list \
    && echo "deb-src http://ppa.launchpad.net/nathan-renniewaldock/flux/ubuntu xenial main" >> /etc/apt-sources.list \
    && apt-get update && apt-get install -y \
    fluxgui \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

ENV HOME /home/flux
RUN useradd --create-home --home-dir $HOME flux \
    && chown -R flux:flux $HOME

WORKDIR $HOME
USER flux

CMD [ "xflux" ]
