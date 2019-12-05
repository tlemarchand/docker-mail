FROM debian:buster-slim

RUN apt-get update && apt-get install -y opendkim && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/Syslog                  yes/Syslog                  no/' /etc/opendkim.conf && \
    sed -i 's/#Mode                   sv/Mode                    s/' /etc/opendkim.conf && \
    echo 'KeyTable        /etc/opendkim/KeyTable' >> /etc/opendkim.conf && \
    echo 'SigningTable    /etc/opendkim/SigningTable' >> /etc/opendkim.conf

CMD /usr/sbin/opendkim -f