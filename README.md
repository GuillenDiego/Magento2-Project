# Magento2-Project
Deploying magento on ec2 and utilizing APIs
```
#!/bin/bash
sudo -i
apt clean all && sudo apt update -y && sudo apt dist-upgrade -y
apt-add-repository ppa:ondrej/php
apt update -y
apt -y install nginx
apt-get -y install php7.2-fpm php7.2-cli
sed -i 's/^memory_limit..*/memory_limit = 2G/' /etc/php/7.2/fpm/php.ini
sed -i 's/^max_execution_time..*/max_execution_time = 1800/' /etc/php/7.2/fpm/php.ini
sed -i 's/^zlib.output_compression..*/zlib.output_compression = On/' /etc/php/7.2/fpm/php.ini
systemctl restart php7.2-fpm
apt -y install mysql-server

```
