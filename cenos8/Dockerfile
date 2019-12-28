FROM centos
LABEL Ken.K
RUN yum -y groupinstall base && yum clean all
RUN yum -y groupinstall development && yum clean all
RUN yum -y groupinstall network-tools && yum clean all
RUN yum -y update && yum clean all
RUN yum -y install langpacks-ja passwd openssh-server epel-release ansible  && yum clean all
RUN mkdir /ansible && \
    alias ls='ls --color=auto'

# 言語を日本語に設定
RUN rm -f /etc/rpm/macros.image-language-conf && \
    sed -i '/^override_install_langs=/d' /etc/yum.conf && \
    yum -y reinstall glibc-common && \
    yum clean all

ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8"

# 日付を日本語に設定
RUN echo 'ZONE="Asia/Tokyo"' > /etc/sysconfig/clock
RUN rm -f /etc/localtime
RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

#CMD --hostname="ansible-centos8" --dns=8.8.8.8 --name ansible-centos8 --priviledge ansible-centos8 /sbin/init