FROM centos:8

# Set up base packages that are expected
RUN dnf -y install openssh-server crontabs NetworkManager firewalld selinux-policy

RUN systemctl mask dev-mqueue.mount dev-hugepages.mount \
     systemd-remount-fs.service sys-kernel-config.mount \
     sys-kernel-debug.mount sys-fs-fuse-connections.mount \
     graphical.target systemd-logind.service \
     NetworkManager.service systemd-hostnamed.service

RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]

RUN systemctl enable sshd

STOPSIGNAL SIGRTMIN+3
RUN mkdir -p /root/.ssh && chmod -R 600 /root/.ssh
COPY id_ed25519.pub /root/.ssh/authorized_keys

RUN chmod 600 /root/.ssh/*
RUN chmod 644 /root/.ssh/authorized_keys

# SSHd setup
EXPOSE 22
CMD ["/usr/sbin/init"]
