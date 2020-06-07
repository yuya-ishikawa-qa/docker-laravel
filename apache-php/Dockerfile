FROM centos:7.4.1708

RUN yum -y update

# リポジトリ epel, remi
RUN yum -y install epel-release
RUN yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

# apacheやphpをインストール
RUN yum -y install httpd
RUN yum -y install --enablerepo=remi,remi-php72 php php-mbstring php-mysqlnd php-pdo php-cli php-common php-devel php-fpm php-gd php-pear php-pecl php-apcu php-xml php-xmlrpc
RUN yum -y install zip unzip

# composerをインストール
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

WORKDIR /var/www/html