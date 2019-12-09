FROM debian:buster-slim

RUN apt-get update && apt-get install -y dkimpy-milter && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/#Mode\t\t\tsv/Mode\t\t\ts/' /etc/dkimpy-milter.conf && \
    echo 'SyslogSuccess\t\t\tyes' >> /etc/dkimpy-milter.conf && \
    sed -i 's/Socket\t\t\tinet:8892@localhost/Socket\t\t\tinet:8892/' /etc/dkimpy-milter.conf && \
    sed -i 's/Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/#Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/' /etc/dkimpy-milter.conf && \
    sed -i 's/UserID\t\t\tdkimpy-milter/#UserID\t\t\tdkimpy-milter/' /etc/dkimpy-milter.conf

USER dkimpy-milter

CMD /usr/bin/dkimpy-milter /etc/dkimpy-milter.conf