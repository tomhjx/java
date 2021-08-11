FROM centos:7

ENV M2_HOME=/usr/local/src/apache-maven
ENV PATH=$M2_HOME/bin:$PATH

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
    yum install -y java-1.8.0-openjdk-devel wget which; \
    java -version; \
    cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime; \
    wget https://archive.apache.org/dist/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.tar.gz; \
    tar -xf apache-maven-3.6.2-bin.tar.gz; \
    mv apache-maven-3.6.2/ /usr/local/src/apache-maven/; \
    chmod +x /usr/local/src/apache-maven/bin/mvn; \
    mvn --version

COPY settings.xml /usr/local/src/apache-maven/conf/settings.xml