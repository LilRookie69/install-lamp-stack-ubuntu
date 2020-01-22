# install-lamp-stack-ubuntu
# Step 1 add ppa
```
apt update;apt -y install software-properties-common;add-apt-repository ppa:ondrej/php --yes;apt update -y;
```
# Step 2 install apache2
```
apt install apache2 -y
```
# Step 3 install php
```
apt install php libapache2-mod-php php-cli php-mysql php-gd php-imagick php-tidy php-xmlrpc php-fpm
```
# Step 4 install mysql
```
apt install mysql-server -y
```
# Settings root password mysql
See your user and password
```
mysql -u root
SELECT user,authentication_string,plugin,host FROM mysql.user;
```
it will show 
```
+------------------+-------------------------------------------+-----------------------+-----------+
| user             | authentication_string                     | plugin                | host      |
+------------------+-------------------------------------------+-----------------------+-----------+
| root             |                                           | auth_socket           | localhost |
| mysql.session    | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| mysql.sys        | *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE | mysql_native_password | localhost |
| debian-sys-maint | *CC744277A401A7D25BE1CA89AFF17BF607F876FF | mysql_native_password | localhost |
+------------------+-------------------------------------------+-----------------------+-----------+
```
than change root password with these command
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```
change the 'password' to anything you want, than flush the previledges with
```
FLUSH PRIVILEGES;
```

# add user/admin account
```
mysql -u root
```
type your password, than add these command
```
ALTER USER 'username'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
GRANT ALL PRIVILEGES ON *.* TO ‘username’@’localhost’;
FLUSH PRIVILEGES;
```



