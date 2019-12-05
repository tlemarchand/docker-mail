FROM debian:buster-slim

RUN apt-get update && apt-get install -y opendkim && \
    rm -rf /var/lib/apt/lists/*

CMD /usr/sbin/opendkim -f -x /etc/opendkim.conf -P /var/run/opendkim/opendkim.pid