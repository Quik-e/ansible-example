# Ubuntu 20.04 Focal Fossa
FROM ubuntu:focal

RUN apt-get update -y && \
apt-get install openssh-server ansible sshpass vim -y && \
mkdir /var/run/sshd && \
echo 'root:P@ssw0rd' | chpasswd && \
sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config &&\
sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config &&\
mkdir /root/.ssh

EXPOSE 22
ENTRYPOINT /etc/init.d/ssh start && tail -f /dev/null
