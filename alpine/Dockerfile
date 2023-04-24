FROM alpine:3.17.3

RUN apk add --no-cache openssh-server sudo python3 && \
    echo 'PasswordAuthentication yes' >> /etc/ssh/sshd_config && \
    adduser -h /home/ansible -s /bin/sh -D ansible wheel && \
    echo 'ansible ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers && \
    echo -n 'ansible:ansible' | chpasswd && \
    ssh-keygen -A && \
    mkdir /var/run/sshd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]