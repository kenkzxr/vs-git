FROM centos:7
LABEL Ken.K
RUN yum -y groupinstall base && yum clean all
RUN yum -y groupinstall development && yum clean all
RUN yum -y groupinstall network-tools && yum clean all
RUN yum -y update && yum clean all
#RUN yum -y install langpacks-ja  && yum clean all
RUN yum -y install passwd openssh-server
RUN yum -y install epel-release && yum clean all
RUN yum -y install ansible --enablerepo=epel && yum clean all
RUN yum clean all && \
    mkdir /ansible

# 言語を日本語に設定
RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8"

# 日付を日本語に設定
RUN echo 'ZONE="Asia/Tokyo"' > /etc/sysconfig/clock
RUN rm -f /etc/localtime
RUN ln -fs /usr/share/zoneinfo/Asia/Tokyo /etc/localtime