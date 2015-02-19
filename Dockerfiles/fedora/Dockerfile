FROM fedora:20
MAINTAINER Azuki

# Let's start with some basic stuff.
RUN yum -y update \
  && yum -y install \
    git \
    docker-io \
    net-tools \
    make \
    tmux \
    e2fsprogs \
  && yum clean all

# libnss-resolver
ENV LIBNSS_VERSION 0.2.1
RUN curl -L https://github.com/azukiapp/libnss-resolver/releases/download/v${LIBNSS_VERSION}/fedora20-libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm -o /tmp/libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm
RUN rpm -i /tmp/libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker"]
