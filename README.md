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
apt-get -y install php7.2-fpm php7.2-cli
```
```
sed -i 's/^memory_limit..*/memory_limit = 2G/' /etc/php/7.2/fpm/php.ini
```
```
sed -i 's/^max_execution_time..*/max_execution_time = 1800/' /etc/php/7.2/fpm/php.ini
```
```
sed -i 's/^zlib.output_compression..*/zlib.output_compression = On/' /etc/php/7.2/fpm/php.ini
```
```
systemctl restart php7.2-fpm
```
```
apt -y install mysql-server
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
apt-get -y install php7.2-fpm php7.2-cli
sed -i 's/^memory_limit..*/memory_limit = 2G/' /etc/php/7.2/fpm/php.ini
sed -i 's/^max_execution_time..*/max_execution_time = 1800/' /etc/php/7.2/fpm/php.ini
sed -i 's/^zlib.output_compression..*/zlib.output_compression = On/' /etc/php/7.2/fpm/php.ini
systemctl restart php7.2-fpm
apt -y install mysql-server

```
