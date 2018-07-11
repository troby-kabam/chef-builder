FROM ubuntu:latest

ENV CHEFDK_VERSION="3.1.0"
ENV CHEFDK_CHECKSUM="ea5eaf7f729f217f5a33722d5b0a8b2aab6acd8f1f096a474eb44e5419bf3144"
ENV CHEFDK_URL="https://packages.chef.io/files/stable/chefdk/${CHEFDK_VERSION}/ubuntu/16.04"
ENV CHEFDK_PACKAGE="chefdk_${CHEFDK_VERSION}-1_amd64.deb"

COPY bash_profile /root/.bash_profile

RUN apt-get update -y && \
    apt-get install -y \
      chef-zero \
      docker.io \
      git \
      vim \
      wget \
      && \
    wget -nv ${CHEFDK_URL}/${CHEFDK_PACKAGE} && \
    echo "${CHEFDK_CHECKSUM}  ${CHEFDK_PACKAGE}" |shasum -a 256 -c - && \
    dpkg -i ${CHEFDK_PACKAGE} && \
    chef gem install kitchen-docker && \
    rm -f ${CHEFDK_PACKAGE} /var/lib/apt/lists/*gz

ENTRYPOINT /bin/bash -l
