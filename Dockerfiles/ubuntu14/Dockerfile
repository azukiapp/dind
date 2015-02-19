FROM ubuntu:14.04
MAINTAINER jerome.petazzoni@docker.com

# Let's start with some basic stuff.
RUN apt-get update -qq \
  && apt-get install -qqy \
    apt-transport-https \
    ca-certificates \
    curl \
    lxc \
    iptables \
    make \
    tmux \
  && apt-get clean -qq \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Install Docker from Docker Inc. repositories.
RUN curl -sSL https://get.docker.com/ubuntu/ | sh

# libnss-resolver
ENV LIBNSS_VERSION 0.2.1
RUN curl -L https://github.com/azukiapp/libnss-resolver/releases/download/v${LIBNSS_VERSION}/ubuntu14-libnss-resolver_${LIBNSS_VERSION}_amd64.deb -o /tmp/libnss-resolver.deb
RUN dpkg -i /tmp/libnss-resolver.deb

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker"]
