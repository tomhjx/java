FROM centos:7
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*;\
    readonly NPROC=$(grep -c ^processor /proc/cpuinfo 2>/dev/null || 1); \
    echo "NPROC=$NPROC"; \
    echo "Installing packages..."; \
    yum install -y java-1.8.0-openjdk; \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime;
    