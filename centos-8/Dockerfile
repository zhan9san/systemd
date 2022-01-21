FROM centos:8
ENV container=docker

# Install systemd -- See https://hub.docker.com/_/centos/
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

RUN yum -y install rpm centos-release \
  && yum -y update \
  && yum -y install sudo

# Install postgres
RUN yum install -y postgresql-server \
  && su - postgres -c '/usr/bin/initdb -D /var/lib/pgsql/data --auth=ident' \
  && systemctl enable postgresql

CMD ["/usr/lib/systemd/systemd"]
