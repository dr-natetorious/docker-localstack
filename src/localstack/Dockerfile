FROM debian:stretch as os_image
LABEL Author="Nate Bachmeier"
LABEL Source="http://github.com/dr-natetorious"

# Common Tooling...
RUN \
  apt-get -y update \
  && apt-get -y install \
    sudo \
    nano \
    curl \
    zip

FROM os_image as build_env
RUN \
  apt-get -y install \
    build-essential \
    make \
    default-jdk \
    maven \
    python3-pip \
  && curl -sL https://deb.nodesource.com/setup_10.x | bash - \
  && apt-get install -y nodejs \
  && curl "https://bootstrap.pypa.io/get-pip.py" -o - | python3

FROM build_env as localstack
RUN \
    pip install localstack