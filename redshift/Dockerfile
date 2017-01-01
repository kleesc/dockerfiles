# Run redshift in a container
#
# docker run -d \
# 	     -v /tmp/.X11-unix/:/tmp/.X11-unix/ \
#	     -e DISPLAY=unix$DISPLAY \
#	     --name redshift \
#	     kleesc/redshift \
#	     redshift \
#	     -l <latitude>:<longitude> \
#	     -b <day_brightness>:<night_brightness>
#
FROM debian:sid
MAINTAINER Kenny Lee Sin Cheong <kenny.lee28@gmail.com>

RUN apt-get update && apt-get install -y \
    redshift \
    --no-install-recommends \
    && rm -rf /var/lib/apt/lists/*

ENV HOME /home/redshift
RUN useradd --create-home --home-dir $HOME redshift \
    && chown -R redshift:redshift $HOME

WORKDIR $HOME
USER redshift

CMD [ "redshift", "-h" ]
