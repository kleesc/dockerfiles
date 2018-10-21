FROM ubuntu:16.04
LABEL maintainer="kenny.lee28@gmail.com"

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    && echo "deb https://qgis.org/debian xenial main" >> /etc/apt/sources.list \
    && echo "deb-src https://qgis.org/debian xenial main" >> /etc/apt/sources.list \
    && apt-key adv --keyserver keyserver.ubuntu.com --recv-key CAEB3DC3BDF7FB45 \
    && apt-get update && apt-get install -y \
    qgis \
    python-qgis \
    qgis-plugin-grass \
    && rm -rf /var/lib/apt/lists/*

ENV HOME /home/qgis
RUN useradd --create-home --home-dir $HOME qgis \
    && chown -R qgis:qgis $HOME

WORKDIR $HOME
USER qgis

CMD ["qgis"]