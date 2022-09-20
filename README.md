# Magento2-Project
Deploying magento on ec2 and utilizing APIs
# Deployment commands
Disabling restart prompt
```
sudo mv /etc/apt/apt.conf.d/99needrestart /home/ubuntu/99needrestart
```
#Updating system
```
sudo apt-get clean all && sudo apt-get update -qq && sudo apt-get dist-upgrade -yy
```
#Add repo for the php package
```
sudo apt-add-repository -y ppa:ondrej/php
```
```
sudo apt-get update -qq
```
```
sudo apt-get -y install nginx
```
```
sudo apt-get -y install php7.2-fpm php7.2-cli
```
```
sudo sed -i 's/^memory_limit..*/memory_limit = 2G/' /etc/php/7.2/fpm/php.ini
```
```
sudo sed -i 's/^max_execution_time..*/max_execution_time = 1800/' /etc/php/7.2/fpm/php.ini
```
```
sudo sed -i 's/^zlib.output_compression..*/zlib.output_compression = On/' /etc/php/7.2/fpm/php.ini
```
```
sudo systemctl restart php7.2-fpm
```
```
sudo apt -y install mysql-server
```

The complete Script
```
#!/bin/bash
# Disabling restart prompt
sudo mv /etc/apt/apt.conf.d/99needrestart /home/ubuntu/99needrestart
#Updating system
sudo apt-get clean all && sudo apt-get update -qq && sudo apt-get dist-upgrade -yy
#Add repo for the php package
sudo apt-add-repository -y ppa:ondrej/php
sudo apt-get update -qq
sudo apt-get -y install nginx
sudo apt-get -y install php7.2-fpm php7.2-cli
sudo sed -i 's/^memory_limit..*/memory_limit = 2G/' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^max_execution_time..*/max_execution_time = 1800/' /etc/php/7.2/fpm/php.ini
sudo sed -i 's/^zlib.output_compression..*/zlib.output_compression = On/' /etc/php/7.2/fpm/php.ini
sudo systemctl restart php7.2-fpm
sudo apt -y install mysql-server
cd /var/www/html
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
composer create-project --repository=https://repo.magento.com/ magento/project-community-edition magento



```
