FROM debian:buster-slim

RUN apt-get update && apt-get install -y opendkim && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/Syslog                  yes/Syslog                  no/' /etc/opendkim.conf && \
    sed -i 's/#Mode                   sv/Mode                    s/' /etc/opendkim.conf && \
    echo 'KeyTable        /etc/opendkim/KeyTable' >> /etc/opendkim.conf && \
    echo 'SigningTable    refile:/etc/opendkim/SigningTable' >> /etc/opendkim.conf && \
    echo 'ExternalIgnoreList      /etc/opendkim/TrustedHosts' >> /etc/opendkim.conf && \
    echo 'InternalHosts           /etc/opendkim/TrustedHosts' >> /etc/opendkim.conf && \
    sed -i 's/#Socket                  inet:8892@localhost/Socket                  inet:8892/' /etc/opendkim.conf && \
    sed -i 's/Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/#Socket                  local:\/var\/run\/opendkim\/opendkim.sock/' /etc/opendkim.conf && \
    sed -i 's/UserID                opendkim/#UserID                opendkim/' /etc/opendkim.conf

USER opendkim

CMD /usr/sbin/opendkim -f