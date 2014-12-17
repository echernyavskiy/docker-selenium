FROM selenium/node-base:2.44.0
MAINTAINER Selenium <selenium-developers@googlegroups.com>

USER root

#=========
# Firefox
#=========
RUN apt-get update -qqy && \
      apt-get -qqy --no-install-recommends install firefox && \
      rm -rf /var/lib/apt/lists/*

#============
# FlashPlayer
#============
RUN apt-get -qqy --no-install-recommends install \
      software-properties-common python-software-properties && \
      add-apt-repository -y ppa:nilarimogard/webupd8 && \
      apt-get update -qqy && \
      apt-get -qqy --no-install-recommends install freshplayerplugin

#========================
# Selenium Configuration
#========================
COPY config.json /opt/selenium/config.json

USER seluser
