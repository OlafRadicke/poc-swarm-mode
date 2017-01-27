# Proof of concept - docker swarm mode with ubuntu cloud images #

## Requirements ##

- genisoimage
- bash
- KVM/libvirt
- wget
- ansible 2.x

## Create KVM VMs with ubuntu cloud images and CloudInit  ##

### Externel documentation ###

- [CloudInit](https://help.ubuntu.com/community/CloudInit)
- [cloudinit](http://cloudinit.readthedocs.io/en/latest/topics/examples.html)
- [CloudInit over webserver](http://foss-boss.blogspot.de/2010/12/cloud-instance-with-cloud-init-on-kvm.html)
- [CloudInit over webserver II](https://pardini.net/blog/2016/11/05/running-ubuntu-cloud-images-with-cloud-init-on-all-infrastructure-from-cloud-to-bare-metal/)

Prepare the cloud-init configurations under ./cloud-init with your public
ssh-key and enter command

```
./script/bootstrap vm
```

This script will download the cloud image of fedora. This can modified in the
file ./script/setup.

A recall of this script will be reset all VMs.

## Create a docker swarm mode cluster ##

Prepare the ./hosts file with the correct IPs of the VMs and tham enter

```
./script/bootstrap swarm
```

This script will be calls the ansible playbook.

# Trouble shooting #

## DependencyWarning ##
```
ImportError: cannot import name DependencyWarning
```
Enter:
```
sudo pip uninstall requests
sudo pip install requests
sudo pip uninstall docopt
sudo pip install docopt
```
And/or try:
```
sudo dnf install python-requests
```
