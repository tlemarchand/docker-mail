FROM debian:buster-slim

RUN apt-get update && apt-get install -y postfix postfix-ldap

CMD postfix start-fg