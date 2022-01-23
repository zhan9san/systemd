FROM centos:7

ENV container docker
LABEL org.opencontainers.image.authors="jack4zhang@gmail.com"

RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y update \
  && yum -y install sudo iproute

# Install postgres
RUN yum install -y postgresql-server \
  && su - postgres -c '/usr/bin/initdb -D /var/lib/pgsql/data --auth=ident' \
  && systemctl enable postgresql

CMD ["/usr/lib/systemd/systemd"]

