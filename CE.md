[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) 

## Using Computing Environments


### A simple node.js web server.


Install node.js in your virtual machine:

```
VM:> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 68576280
VM:> sudo apt-add-repository "deb https://deb.nodesource.com/node_7.x $(lsb_release -sc) main"
VM:> sudo apt-get update
VM:> sudo apt-get install nodejs
```

On your VM, change into `~/code/projects/express`. Run `npm install`.

Start the webserver.

```
VM:> npm run forever
```

Open a browser on your host. You should see your webserver running on 192.168.33.10:3000

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

### A python jupyter notebook

```
sudo apt-get install python-dev python-pip
sudo pip install --upgrade pip 
sudo apt-get install jupyter

jupyter notebook --ip 0.0.0.0
```
