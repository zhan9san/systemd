FROM ubuntu:18.04

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
     systemd systemd-cron sudo iproute2 postgresql\
  && rm -Rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

CMD ["/sbin/init"]
