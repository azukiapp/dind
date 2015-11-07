FROM fedora:20
MAINTAINER Azuki <support@azukiapp.com>

# Let's start with some basic stuff.
RUN yum -y update \
  && yum -y install \
    git \
    net-tools \
    make \
    tmux \
    e2fsprogs \
  && curl -sSL https://get.docker.com/ | sh \
  && yum clean all

# libnss-resolver
ENV LIBNSS_VERSION 0.3.0
RUN curl -L https://github.com/azukiapp/libnss-resolver/releases/download/v${LIBNSS_VERSION}/fedora20-libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm -o /tmp/libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm \
  && rpm -i /tmp/libnss-resolver-${LIBNSS_VERSION}-1.x86_64.rpm

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker"]
