# Run lepton in a container
#
# docker run --rm \
# 	     -v /data:/data \
#	     --name lepton \
#	     kleesc/lepton \
#	     picture.jpg
#
FROM debian:sid
MAINTAINER Kenny Lee Sin Cheong <kenny.lee28@gmail.com>

WORKDIR /tmp/

RUN apt-get update && apt-get install -y \
    apt-transport-https \
    ca-certificates \
    build-essential \
    git \
    curl \
    python \
    dh-autoreconf \
    --no-install-recommends

RUN git clone https://github.com/dropbox/lepton.git \
    && cd lepton \
    && git checkout tags/1.2.1 \
    && ./autogen.sh \
    && ./configure \
    && make \
    && make check \
    && mv lepton /usr/bin/lepton


FROM debian:sid-slim
WORKDIR /data
COPY --from=0 /usr/bin/lepton /usr/bin/lepton
ENTRYPOINT ["lepton"]
