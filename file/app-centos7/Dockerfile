FROM centos:7

# ユーザー設定
ARG APP_USER="app-user"
ARG PASSWD="user-password"

# yum update
RUN yum -y update

# useradd
RUN useradd -m $APP_USER && \
    echo "$APP_USER:$PASSWD" | chpasswd

# sudo設定
RUN yum -y install sudo && \
    echo "$APP_USER ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

# ssh install
RUN yum -y install openssh-server openssh-clients
# .ssh内ファイル配置＆権限付与
RUN mkdir /home/$APP_USER/.ssh
COPY app-home/ /home/$APP_USER/
RUN chown -R $APP_USER:$APP_USER /home/$APP_USER && \
    chmod 0700 /home/$APP_USER/.ssh &&  \
    find /home/$APP_USER/.ssh -type f | xargs chmod 0600

# yum clean
RUN yum clean all
