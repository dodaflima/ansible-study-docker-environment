FROM ubuntu:20.04

RUN apt update && \
    apt install --no-install-recommends openssh-server sudo python3 -y && \
    useradd -d /home/ansible -G sudo -s /bin/sh ansible && \
    echo -n "ansible:ansible" | chpasswd && \
    echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config && \
    echo "ansible ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers && \
    mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]