FROM centos:7

# ユーザー設定
ARG ANSIBLE_USER="ansible-user"
ARG APP_USER="app-user"
ARG PASSWD="user-password"

# yum update
RUN yum -y update
# epelリポジトリを追加しansibleインストール
RUN yum -y install epel-release
RUN yum -y install ansible
# jenkins install
RUN yum -y install wget
RUN yum -y install java-11-openjdk
RUN yum -y install initscripts
RUN wget --no-check-certificate -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
RUN rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
RUN yum -y install jenkins

# useradd
RUN useradd -m $ANSIBLE_USER && \
    echo "$ANSIBLE_USER:$PASSWD" | chpasswd
RUN useradd -m $APP_USER && \
    echo "$APP_USER:$PASSWD" | chpasswd

# sudo設定
RUN yum -y install sudo && \
    echo "Defaults:jenkins !requiretty" >> /etc/sudoers && \
    echo "jenkins ALL=($ANSIBLE_USER) NOPASSWD: /bin/bash" >> /etc/sudoers && \
    echo "$APP_USER ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# ssh install
RUN yum -y install openssh-server openssh-clients
# .ssh内ファイル配置＆権限付与
RUN mkdir /home/$ANSIBLE_USER/.ssh
COPY ansible-home/ /home/$ANSIBLE_USER/
RUN chown -R $ANSIBLE_USER:$ANSIBLE_USER /home/$ANSIBLE_USER && \
    chmod 0700 /home/$ANSIBLE_USER/.ssh &&  \
    find /home/$ANSIBLE_USER/.ssh -type f | xargs chmod 0600

# yum clean
RUN yum clean all
