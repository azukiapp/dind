FROM fedora:20
MAINTAINER everton@azukiapp.com

# Let's start with some basic stuff.
RUN yum -y update; yum clean all
RUN yum -y install git docker-io net-tools make; yum clean all

# libnss-resolver
RUN curl -L https://github.com/azukiapp/libnss-resolver/releases/download/v0.2.1/fedora20-libnss-resolver-0.2.1-1.x86_64.rpm -o /tmp/fedora20-libnss-resolver-0.2.1-1.x86_64.rpm
RUN rpm -i /tmp/fedora20-libnss-resolver-0.2.1-1.x86_64.rpm

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker"]

