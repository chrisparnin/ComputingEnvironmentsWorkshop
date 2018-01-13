[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) | [Baker](Baker.md)

## Using Computing Environments

### A simple node.js web server.

Install node.js in your virtual machine:

```
VM:> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 68576280
VM:> sudo apt-add-repository "deb https://deb.nodesource.com/node_7.x $(lsb_release -sc) main"
VM:> sudo apt-get update
VM:> sudo apt-get install nodejs
```

On your VM, change into `/vagrant/projects/express/`. Run `npm install`.

Start the webserver.

```
VM:> npm run forever
```

Open a browser on your host. You should see your webserver running on `192.168.33.10:3000`

#### Windows warning

If you run `npm install` you may see some errors due to symlinks not being able to be created in a synced_folder. Solution: Make sure you start the VM with admin permissions, by running `vagrant up` within an Admin Cmd window.

#### About forever

Forever is a utility tool for running a node program as a long-running service. There are two reasons to use forever: 1) If the process dies, it will restart the process. 2) If you exit the shell, it will keep running the process as long as the VM is running.

#### Making changes

1. Update the code to print a different message.
2. Update the package.json to run a new command, called, `stop`, which will run, `forever stopall`.
3. Restart the server process with command: `npm run stop`, and start again with `npm run forever`.
4. Check for your updated code in the browser.



### A python jupyter notebook

```
sudo apt-get install python-dev python-pip
sudo pip install --upgrade pip 
sudo -H pip install jupyter

jupyter notebook --ip 0.0.0.0
```
