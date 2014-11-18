FROM ubuntu:14.04
MAINTAINER jerome.petazzoni@docker.com

# Let's start with some basic stuff.
RUN apt-get update -qq
RUN apt-get install -qqy iptables ca-certificates lxc make

# Install Docker from Docker Inc. repositories.
RUN apt-get install -qqy apt-transport-https
RUN echo deb https://get.docker.io/ubuntu docker main > /etc/apt/sources.list.d/docker.list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 36A1D7869245C8950F966E92D8576A8BA88D21E9
RUN apt-get update -qq
RUN apt-get install -qqy lxc-docker
RUN apt-get install -qqy git curl \
                         man tmux make

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

