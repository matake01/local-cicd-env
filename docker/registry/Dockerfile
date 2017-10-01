# URL: http://www.macadamian.com/2017/02/07/creating-a-private-docker-registry/

FROM registry:2.5.1

MAINTAINER Mathias Åkerberg <maker@payer.se>

# Add user accounts
RUN mkdir -p /htpasswd_storage
COPY htpasswd /htpasswd_storage/htpasswd

COPY custom-entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh
