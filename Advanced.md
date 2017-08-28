### A mysql server

```
wget http://dev.mysql.com/get/mysql-apt-config_0.8.1-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.1-1_all.deb

sudo echo mysql-apt-config mysql-apt-config/select-server select mysql-5.7 | sudo debconf-set-selections
sudo echo mysql-server mysql-server/root_password password mypass | sudo debconf-set-selections  
sudo echo mysql-server mysql-server/root_password_again password mypass | sudo debconf-set-selections

sudo apt-get update
sudo apt-get install mysql-server
```

