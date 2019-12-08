FROM debian:buster-slim

RUN apt-get update && apt-get install -y opendkim && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/Syslog\t\t\tyes/Syslog\t\t\tno/' /etc/opendkim.conf && \
    sed -i 's/#Mode\t\t\tsv/Mode\t\t\ts/' /etc/opendkim.conf && \
    echo 'KeyTable\t\t\t/etc/opendkim/KeyTable' >> /etc/opendkim.conf && \
    echo 'SigningTable\t\t\trefile:/etc/opendkim/SigningTable' >> /etc/opendkim.conf && \
    echo 'ExternalIgnoreList\t\t\t/etc/opendkim/TrustedHosts' >> /etc/opendkim.conf && \
    echo 'InternalHosts\t\t\t/etc/opendkim/TrustedHosts' >> /etc/opendkim.conf && \
    sed -i 's/#Socket                  inet:8892@localhost/Socket\t\t\tinet:8892/' /etc/opendkim.conf && \
    sed -i 's/Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/#Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/' /etc/opendkim.conf && \
    sed -i 's/UserID                opendkim/#UserID\t\t\topendkim/' /etc/opendkim.conf

USER opendkim

CMD /usr/sbin/opendkim -f