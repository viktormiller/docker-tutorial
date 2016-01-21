# docker-tutorial
A short Tutorial for using Docker with Vagrant

## Getting Started  
1. [Download VirtualBox (5.0.14)][1]
2. [Download Vagrant (1.8.1)][2]

After you installed Vagrant a reboot is required.

## Example 1
### 1. Create a project folder
Create a file called `Vagrant`
```yml
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "puphpet/ubuntu1404-x64"

  config.vm.provision "docker" do |d|
    d.run "tutum/wordpress", args: "-p '80:80'"
  end

  config.vm.network "forwarded_port", guest: 80, host: 8080

end
```

Start the virtual machine by typing `vagrant up`

Now open the Browser and type <http://localhost:8080/>

## Example 2
1. SSH into your virtual machine using [putty](http://www.putty.org/).  
2. Stop the running container by typing `docker stop tutum-wordpress`

[1]: https://www.virtualbox.org/wiki/Downloads
[2]: https://www.vagrantup.com/downloads.html
