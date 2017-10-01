FROM jenkins:2.60.2

MAINTAINER Mathias Åkerberg <maker@payer.se>

ENV DEBIAN_FRONTEND noninteractive
ENV DEBCONF_NONINTERACTIVE_SEEN true

# Install necessary packages
USER root

RUN apt-get update \
      && apt-get install -y \
      maven

#======================================#
# Xvfb + Chromium for Selenium Testing #
#======================================#
RUN apt-get update \
  && apt-get install -y \
  curl \
  xvfb x11-xkb-utils xfonts-100dpi xfonts-75dpi xfonts-scalable xfonts-cyrillic dbus-x11 libfontconfig1-dev \
  chromium ca-certificates

ADD xvfb-chromium /usr/bin/xvfb-chromium
RUN ln -s /usr/bin/xvfb-chromium /usr/bin/chromium-browser

RUN \
  wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
  echo "deb http://dl.google.com/linux/chrome/deb/ stable main" > /etc/apt/sources.list.d/google.list && \
  apt-get update && \
  apt-get install -y google-chrome-stable && \
  rm -rf /var/lib/apt/lists/*

#=====================#
# Chrome webdriver    #
#=====================#
ARG CHROME_DRIVER_VERSION=2.31
RUN wget --no-verbose -O /tmp/chromedriver_linux64.zip https://chromedriver.storage.googleapis.com/$CHROME_DRIVER_VERSION/chromedriver_linux64.zip \
  && rm -rf /opt/selenium/chromedriver \
  && unzip /tmp/chromedriver_linux64.zip -d /opt/selenium \
  && rm /tmp/chromedriver_linux64.zip \
  && mv /opt/selenium/chromedriver /opt/selenium/chromedriver-$CHROME_DRIVER_VERSION \
  && chmod 755 /opt/selenium/chromedriver-$CHROME_DRIVER_VERSION \
  && ln -fs /opt/selenium/chromedriver-$CHROME_DRIVER_VERSION /usr/bin/chromedriver

ENV SELENIUM_WEBDRIVER_PATH /usr/bin/chromedriver

# Make sure jenkins user has docker privileges
# Notice: the group ID for docker group on my Ubuntu is 125, therefore I can only run docker commands if I have same group id inside.
# Otherwise the socket file is not accessible.
#
# RUN groupadd -g 135 docker && usermod -a -G docker jenkins
# USER jenkins

# Enable STARTTLS for SMTP
ENV JAVA_OPTS -Dmail.smtp.starttls.enable=true
