# Development

## Vagrant

Vagrant orchestrates local vm's with a config file saved in the git
repository. This file is called `Vagrantfile`.

To install _vagrant_ follow the
[online-instruction](https://www.vagrantup.com/).

To start a virtual machine with the current deployment you can use the
`up` command.

```bash
# Start virtual machine a do initial deployment
vagrant up
```

After the first deployment the config changes can be applied quickly
without destroying the current machine. This allows to test small
changes often, which reduces the error rate.

```bash
# You can rerun the ansible configuration with
vagrant provision
```

Update all project files currently residing in the wm to match the
project files.

```bash
# Update files in VM:
vagrant rsync
```
Shutdown and remove all data stored in the guest.

```bash
# Destroy the VM if you are done:
vagrant destroy
```

## Vagrant KVM

In order to use _Vagrant_ you need _VirtualBox_ installed. When
_VirtualBox_ is not installed or unavailable on a kernel or distribution
the local deployment will not work.

As an alternative to _VirtualBox_, there exists a _Vagrant_ backend
which supports _KVM_. This feature is only available for _Linux_
operating systems.

For more information and a detailed installation guide, have a look at
the [vagrant-libvirt github repository](www.github.com/vagrant-libvirt/vagrant-libvirt).

## Server Deployment

Currently not implemented, only deployment to vagrant is running.

## Encryption

The secrets are all saved in plain sight. An ansible-vault secrets file
stores them encrypted with a password. This file is checked in the git
repository, therefore the passwords are versioned.