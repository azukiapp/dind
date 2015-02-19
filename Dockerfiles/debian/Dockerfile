FROM golang:1.3.3-cross
MAINTAINER Azuki

# Install Docker
RUN apt-get update -qq
RUN apt-get install -qqy docker.io make git curl man tmux

# Install the magic wrapper.
ADD ./wrapdocker /usr/local/bin/wrapdocker
RUN chmod +x /usr/local/bin/wrapdocker

# Define additional metadata for our image.
VOLUME /var/lib/docker
CMD ["wrapdocker"]
