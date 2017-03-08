#ubuntu 14.04 with mysql and nginx just the way we love it
FROM ubuntu:14.04

#install 
RUN sudo apt-get -y update && sudo apt-get install -y vim joe mc htop nginx php5-fpm php5-cli php5-mcrypt php5-gd redis-server curl php5-curl php5-mysql mysql-server rubygems-integration ruby ruby-compass && curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/local/bin --filename=composer && gem install compass && gem install zurb-foundation && gem install susy

RUN sudo php5enmod mcrypt

CMD tail -f /dev/null
