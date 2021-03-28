FROM centos:7.4.1708
RUN yum -y update

# リポジトリ epel, remi
RUN yum -y install epel-release
RUN yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

# apacheやphpをインストール
RUN yum -y install httpd
RUN yum -y install --enablerepo=remi,remi-php74 php php-mbstring php-mysqlnd php-pdo php-cli php-common php-devel php-fpm php-gd php-pear php-pecl php-apcu php-xml php-xmlrpc
RUN yum -y install zip unzip
RUN curl -sL https://rpm.nodesource.com/setup_14.x | bash -
RUN yum -y install nodejs
# node command
COPY --from=node:14.16 /usr/local/bin /usr/local/bin
# npm command
COPY --from=node:14.16 /usr/local/lib /usr/local/lib
# yarn command
COPY --from=node:14.16 /opt /opt

# composerをインストール
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

WORKDIR /var/www/html
