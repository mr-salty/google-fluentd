FROM centos:8

RUN yum -y update \
 && yum -y install \
        # Needed for gpg2 and rvm installation.
        curl \
        # Needed for agent build.
        autoconf \
        bzip2 \
        expect \
        gcc-c++ \
        git \
        patch \
        rpm-build \
        rpm-sign \
        ruby \
        which \
        zlib-devel \
 # RVM GPG keys.
 && mkdir -p ~/.gnupg && echo "disable-ipv6" >> ~/.gnupg/dirmngr.conf \
 && gpg2 --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB \
 && (curl -sSL https://get.rvm.io | /bin/bash -s stable) \
 # RVM requires running in a login shell.
 && /bin/bash -l -c "rvm requirements && rvm install 2.5.3 && gem install bundler --no-document && gem update" \
 && yum -y clean all
