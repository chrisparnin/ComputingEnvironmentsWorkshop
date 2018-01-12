[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) | [Baker](Baker.md)

## Using Baker

#### Prereqs

To run baker, you will need vagrant and virtual box on your system. See [VM instructions](VM.md) if you have not installed these tools.

Install Baker by following the instructions on [Baker documentation](https://docs.getbaker.io/installation/).

#### First time setup.

Setup `baker` (installs a local ansible server to manage configuration of your VMs.)

```
baker setup
```

#### Creating a VM with baker

You want to create a computing environment for a project hosted on github. This [repo](https://github.com/ottomatica/baker-test/) has code for running a simple node.js web server. 

Run the following

```
baker bake --repo https://github.com/ottomatica/baker-test
```

You will be prompted to provide two values. While you can change these values, you can use the following default values:

*how much memory?* 1024  
*Port for express server?* 9000  

If something goes wrong, and you want to run again, you can switch over to the "local" version of the command, to reinitialized the baker-test directory: `baker bake --local baker-test/`

#### Test it out

This will clone a git repo into the `baker-test` and create a VM to run configured to run the server. You can checkout the node server by visiting `127.0.0.1:9000` in your web browser.

Cool. You can ssh into the VM by just running `baker ssh baker-test`. baker will automatically create a synced_folder for you. Just go to `cd /baker-test`.


