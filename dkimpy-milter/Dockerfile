FROM debian:bullseye-slim

COPY dkimpy-milter/version /tmp/

RUN apt-get update && apt-get install -y dkimpy-milter=`cat /tmp/version` && \
    rm -rf /var/lib/apt/lists/* && \
    sed -i 's/#Mode\t\t\tsv/Mode\t\t\ts/' /etc/dkimpy-milter/dkimpy-milter.conf && \
    echo 'SyslogSuccess\t\t\tyes' >> /etc/dkimpy-milter/dkimpy-milter.conf && \
    sed -i 's/Socket\t\t\tinet:8892@localhost/Socket\t\t\tinet:8892/' /etc/dkimpy-milter/dkimpy-milter.conf && \
    sed -i 's/Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/#Socket\t\t\tlocal:\/var\/run\/opendkim\/opendkim.sock/' /etc/dkimpy-milter/dkimpy-milter.conf && \
    sed -i 's/UserID\t\t\tdkimpy-milter/#UserID\t\t\tdkimpy-milter/' /etc/dkimpy-milter/dkimpy-milter.conf

USER dkimpy-milter

CMD /usr/bin/dkimpy-milter /etc/dkimpy-milter/dkimpy-milter.conf