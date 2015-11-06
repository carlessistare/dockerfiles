FROM sequenceiq/spark:1.5.1

MAINTAINER Carles Sistare <carles.sistare@gmail.com>

ENV JDK_FILE=jdk-8u66-linux-x64.tar.gz

WORKDIR /opt

# INSTALL WGET
RUN curl https://bintray.com/sbt/rpm/rpm | tee /etc/yum.repos.d/bintray-sbt-rpm.repo && \
    yum install -y wget sbt  && \
    wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u66-b17/${JDK_FILE}" && \
    tar xzf ${JDK_FILE} && \
    alternatives --install /usr/bin/java java /opt/jdk1.8.0_66/bin/java 1 && \
    alternatives --set java /opt/jdk1.8.0_66/bin/java && \
    rm ${JDK_FILE}

RUN sbt sbtVersion && \
    mkdir /workdir

WORKDIR /workdir

CMD ["sbt", "clean test package"]