FROM debian:buster-slim

RUN apt-get update && apt-get install -y dovecot-core dovecot-gssapi dovecot-imapd dovecot-ldap dovecot-lmtpd dovecot-managesieved dovecot-sieve dovecot-submissiond && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/ssl = yes/ssl = no/' /etc/dovecot/conf.d/10-ssl.conf

USER dovecot

CMD /usr/sbin/dovecot -F