FROM ubuntu:trusty

COPY bootstrap.sh /

RUN apt-get update -y && \
    apt-get install -y \
      chef-zero \
      wget \
      && \
    chmod a+x /bootstrap.sh && \
    wget https://packages.chef.io/files/stable/chefdk/2.5.3/ubuntu/14.04/chefdk_2.5.3-1_amd64.deb && \
    echo "export PS1='$? \u@\h \w\\$ '" >>/root/.bash_profile

ENTRYPOINT /bootstrap.sh
