FROM ubuntu:14.04
 RUN sudo apt-get -y update && sudo apt-get install -y vim joe mc htop  nginx php5-fpm php5-cli php5-mcrypt php5-gd redis-server curl
 
 VOLUME /var/lib/mysql
 EXPOSE 80 3306
 
 CMD tail -f /dev/null
