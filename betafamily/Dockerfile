FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive
ENV CHE_MYSQL_PASSWORD=root
ENV CHE_MYSQL_DB=thebetafamily
ENV CHE_MYSQL_USER=root

#install 
RUN sudo apt-get -y update && sudo apt-get install -y vim joe mc htop nginx php5-fpm php5-cli php5-mcrypt php5-gd redis-server curl php5-curl php5-mysql mysql-server rubygems-integration ruby ruby-compass
RUN RUN curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer && gem install compass && gem install zurb-foundation && gem install susy
RUN sudo php5enmod mcrypt && restart php-fpm

RUN sudo service mysql start
#&& sudo sed -i.bak 's/127.0.0.1/0.0.0.0/g' /etc/mysql/my.cnf && sudo service mysql restart

RUN sudo mysql -uroot -e "GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'; FLUSH PRIVILEGES;"
RUN sudo service mysql restart
RUN sudo service mysql restart && sudo mysql -uroot -e "CREATE USER '$CHE_MYSQL_USER'@'%' IDENTIFIED BY '"$CHE_MYSQL_PASSWORD"'"
RUN sudo mysql -uroot -e "GRANT ALL PRIVILEGES ON *.* TO '$CHE_MYSQL_USER'@'%' IDENTIFIED BY '"$CHE_MYSQL_PASSWORD"'; FLUSH PRIVILEGES;"
RUN sudo mysql -uroot -e "CREATE DATABASE $CHE_MYSQL_DB;"
 
# label is used in Servers tab to display mapped port for Apache process on 80 port in the container
LABEL che:server:80:ref=nginx che:server:80:protocol=http
 
VOLUME /var/lib/mysql
EXPOSE 80
 
CMD  sudo service mysql start && sudo service nginx start && tail -f /dev/null
