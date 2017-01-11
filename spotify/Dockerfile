FROM debian:sid
MAINTAINER Kenny Lee Sin Cheong <kenny.lee28@gmail.com>

RUN apt-get update && apt-get install -y \
    dirmngr \
    gnupg \
    --no-install-recommends \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys BBEBDCB318AD50EC6865090613B00F1FD2C19886 \
    && echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list.d/spotify.list \
    && echo "deb http://ftp.de.debian.org/debian jessie main " >> /etc/apt/sources.list.d/workaround.list \
    && apt-get update && apt-get install -y \
    alsa-utils \
    libgl1-mesa-dri \
    libgl1-mesa-glx \
    libpangoxft-1.0-0 \
    libssl1.0.0 \
    libssl1.0.2 \
    libxss1 \
    spotify-client \
    xdg-utils \
    pulseaudio \
    xauth \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*


ADD start-spotify /usr/bin/start-spotify
RUN chmod +x /usr/bin/start-spotify

ENV HOME /home/spotify
RUN useradd --create-home --home-dir $HOME spotify \
    && gpasswd -a spotify audio \
    && chown -R spotify:spotify $HOME

USER spotify
WORKDIR $HOME

RUN echo "QLineEdit { color: #000 }" > /home/spotify/spotify-override.css

CMD [ "start-spotify" ]
