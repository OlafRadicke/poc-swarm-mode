# Proof of concept - docker swarm mode #

## Requirements ##

- genisoimage
- bash
- KVM/libvirt
- wget
- ansible 2.x

## Create KVM VMs with fedora cloud images and cloud-config  ##

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
