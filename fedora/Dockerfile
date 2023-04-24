FROM fedora:39

RUN dnf -y install openssh-server sudo python3 && \
    useradd -s /bin/bash -d /home/ansible -G wheel ansible && \
    echo -n "ansible:ansible" | chpasswd && \
    echo 'ansible ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers && \
    sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config && \
    ssh-keygen -A && \
    mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]