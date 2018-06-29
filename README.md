### What is it?
A Vagrant configuration that starts up a PostgreSQL database in a virtual machine for local development.

### Installation
- Install [Vagrant](https://www.vagrantup.com/downloads.html) and [Virtual Box](https://www.virtualbox.org/wiki/Downloads).
- Clone the repo
- (Optional) Add the proxy address in *Vagrantfile* if needed
- (Optional) Edit *scripts/postgresql.sh* (db credentials mostly)
- $ vagrant up (start the virtual machine)
- $ vagrant halt (stop the virtual machine)
