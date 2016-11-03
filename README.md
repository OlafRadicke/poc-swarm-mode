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
./script/setup
```

This script will download the cloud image of fedora. This can modified in the
file ./script/setup.

A recall of this script will be reset all VMs.

## Create a docker swarm mode cluster ##

Prepare the ./hosts file with the correct IPs of the VMs and tham enter

```
./script/bootstrap
```

This script will be calls the ansible playbook.
