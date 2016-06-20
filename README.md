# 'Angular2 on CentOS' Vagrant box

Just a Vagrant box for getting started with Angular2 and node.js and CentOS.

I followed the tutorial on [angular.io](https://angular.io/docs/ts/latest/quickstart.html).

Ports 3000 and 3001 from the VM are forwarded to the same ports on the host. So you can access lite-server and its web UI running on the VM at http://localhost:3000 and http://localhost:3001.


## Prerequisites

To rig up the VM, you need Vagrant (version 1.8 or newer, along with virtualbox or libvirt) and ansible (version 2.0 or newer).

The roles I downloaded from ansible galaxy (check [vm_provision/requirements.yml](vm_provision/requirements.yml)) are included in this repository. I have not modified them. I downloaded them like so:

```
cd vm_provision
ansible-galaxy install -r requirements.yml -p roles/
```

## VM up and down
```
vagrant up
vagrant ssh
vagrant destroy -f
```

## VM help
```
vagrant help
```


## Notes

### CentOS on vagrant: official image vs geerlingguy

I used geerlingguy's CentOS 7 vagrant box instead of the official one because the offical one doesn't have VirtualBox guest additions installed. So with the offical one you don't get shared directories, which sucks. It is of course possible to automatically install VBox guest additions into the official CentOS VM: [this](https://github.com/lpancescu/cloud-instance-starter-kit) ansible role does it.

Should you switch to the offical image, note that the project directory is mapped to `/home/vagrant/sync` (see [https://seven.centos.org/2016/06/updated-centos-vagrant-images-available/](https://seven.centos.org/2016/06/updated-centos-vagrant-images-available/)) in the official image, not `/vagrant` which is Vagrant's default.
