FROM registry.access.redhat.com/ubi8/ubi

ENV container docker

RUN yum -y update &&     yum -y install vim curl openssh-server openssh-clients sudo passwd &&     yum clean all

RUN useradd -m -s /bin/bash gurus &&     echo "gurus:Santhi@1481#" | chpasswd &&     echo "gurus ALL=(ALL) ALL" >> /etc/sudoers

RUN ssh-keygen -A

RUN mkdir -p /home/gurus/.ssh &&     chmod 700 /home/gurus/.ssh &&     ssh-keygen -t rsa -f /home/gurus/.ssh/id_rsa -N "" &&     cat /home/gurus/.ssh/id_rsa.pub >> /home/gurus/.ssh/authorized_keys &&     chmod 600 /home/gurus/.ssh/authorized_keys &&     chown -R gurus:gurus /home/gurus/.ssh

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
