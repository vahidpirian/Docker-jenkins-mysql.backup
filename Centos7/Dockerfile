FROM centos:7

MAINTAINER "vahidpirian"

RUN yum install -y openssh-server

RUN useradd jenkins && \
    echo "jenkinspass" | passwd jenkins --stdin && \
    mkdir /home/jenkins/.ssh && \
    chmod 700 /home/jenkins/.ssh

COPY jenkins-key.pub /home/jenkins/.ssh/authorized_keys

RUN chown jenkins:jenkins -R /home/jenkins/.ssh/ && \
    chmod 600 /home/jenkins/.ssh/authorized_keys

# install mysql client
RUN yum install -y mysql

RUN /usr/sbin/sshd-keygen

CMD /usr/sbin/sshd -D
