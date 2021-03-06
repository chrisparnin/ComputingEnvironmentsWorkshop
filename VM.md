[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) | [Baker](Baker.md)

## Virtual Machines

Let's try creating a Ubuntu 14.04 virtual machine using vagrant.

### PreReqs

* Install [vagrant](https://www.vagrantup.com/downloads.html).
* Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) is a recommended provider.
  Other [virtual machine providers](https://docs.vagrantup.com/v2/providers/) do exist.

#### Windows help

* If you're running Hyper-V and VirtualBox, and you're experiencing crashes when you try to start a VM, you may need to turn off Hyper-V (which exclusively locks use of CPU for virtualization).
* If you can't run vagrant ssh, Add `C:\Program Files\Git\usr\bin` to your PATH, which includes `ssh`.


### Creating a Virtual Machine

#### Try it out

Initialize a virtual machine. `ubuntu/trusty64` is one default image. A list of other virtual machine images can be found [here](https://atlas.hashicorp.com/boxes/search).

    vagrant init ubuntu/trusty64

Start up the virtual machine.

    vagrant up

Then    

    vagrant ssh

You should be able to connect to the machine.

#### How it works...

When you create a VM with vagrant, vagrant will interact with a virtualization provider, such as VirtualBox to do the heavy-lifting. Vagrant is only a useful utility tool for coordinating the management of VMs. To store information about the VM, it will create a Vagrantfile in your current directory as well as a hidden directory (`.vagrant`).

Vagrant only allows one virtual machine configuration per directory. You will want to organize your VMs, so you store multiple images in one place. For example in a directory (`/boxes`):

### Customizing Your Virtual Machine

The Vagrantfile will contain some settings you can adjust for memory, networking, etc.
Two customizations you may consider making if working with your VM long-term:


#### Virtualbox Networking

In virtualbox, VMs typically have [four ways](http://catlingmindswipe.blogspot.com/2012/06/how-to-virtualbox-networking-part-two.html) to set up the network:
- Network Address Translation (NAT), *which is the default*,
- Bridged,
- Internal network
- Host Only (Recommended).

Private networking (Host-only) is the recommended setting for Linux/Mac/Windows 10. **Bonus**: You can use hard-coded ip address in your scripts. Uncomment the following line in Vagrantfile:


```ruby
# Ensure this line is uncommented in your Vagrantfile 
config.vm.network "private_network", ip: "192.168.33.10"
```

Then run, `vagrant reload`. 

#### Enabling easy workflow, fixing some issues.

* 1) Enable a synced folder. This will allow you to edit code/files from editors in your host OS.
* 2) Fix DNS to use the same as your host OS instead of its own.

```ruby
  # Important, you must run vagrant in an admin shell if you want symlinks to work correctly.
  # i.e., for npm install to work properly, you must have vagrant provision the machine in admin cmd prompt.
  config.vm.synced_folder "C:/dev", "/vol/dev"
  config.vm.synced_folder "C:/projects", "/vol/projects"

  config.vm.provider :virtualbox do |vb|
     # fix crappy dns
     # https://serverfault.com/questions/453185/vagrant-virtualbox-dns-10-0-2-3-not-working
     vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
```


