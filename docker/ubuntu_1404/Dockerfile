FROM ubuntu:latest

ENV CHEFDK_URL="https://packages.chef.io/files/stable/chefdk/2.5.3/ubuntu/16.04"
ENV CHEFDK_PACKAGE="chefdk_2.5.3-1_amd64.deb"
ENV CHEFDK_CHECKSUM="b6cd2c84e2ecbf35238dd6c360eadbab89f44e1c5a7b54430828529fa403204f"

RUN apt-get update -y && \
    apt-get install -y \
      chef-zero \
      docker.io \
      git \
      wget \
      && \
    wget -nv ${CHEFDK_URL}/${CHEFDK_PACKAGE} && \
    echo "${CHEFDK_CHECKSUM}  ${CHEFDK_PACKAGE}" |shasum -a 256 -c - && \
    dpkg -i ${CHEFDK_PACKAGE} && \
    chef gem install kitchen-docker && \
    rm -f ${CHEFDK_PACKAGE} /var/lib/apt/lists/*gz && \
    echo "export PS1='$? \u@\h \w\\$ '" >>/root/.bash_profile

ENTRYPOINT /bin/bash -l
