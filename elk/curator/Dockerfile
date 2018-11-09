# escape=`
FROM python:2.7-alpine3.6 as base-curator
LABEL mantainer="Eduardo Santos<eduardo.s.dos.santos@accenture.com>"

RUN apk update `
  && apk add shadow `
  && groupadd -r curator && useradd -r -g curator curator `
  && pip install elasticsearch-curator

RUN mkdir -p /var/log/cron && mkdir -m 0644 -p /var/spool/cron/crontabs && touch /var/log/cron/cron.log && mkdir -m 0644 -p /etc/cron.d

# COPY ./curator/config/delete_indices_cron /var/spool/cron/crontabs/delete_indices_cron
COPY ./curator/config /opt/config

COPY ./curator/docker-entrypoint.sh /
COPY ./curator/docker-cmd.sh /

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/docker-cmd.sh"]
