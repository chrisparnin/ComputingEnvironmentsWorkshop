[Virtual Machines](VM.md) | [Using Computing Environments](CE.md) 

## Using Computing Environments

### Setuping more

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


iPython for Dazed example.

