FROM debian:buster

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
  && apt-get install -y --no-install-recommends python sudo systemd systemd-sysv postgresql \
  && rm -rf /var/lib/apt/lists/* \
  && rm -Rf /usr/share/doc && rm -Rf /usr/share/man \
  && apt-get clean

# Make sure systemd doesn't start gettys on tty
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

CMD ["/sbin/init"]
