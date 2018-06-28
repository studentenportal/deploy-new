# Development

## Test deployment locally with Vagrant

- Install [Vagrant](https://vagrantup.com/)

```bash
# Start virtual machine a do initial deployment
vagrant up

# You can rerun the ansible configuration with
vagrant provision

# Update files in VM:
vagrant rsync

# Destroy the VM if you are done:
vagrant destroy
```
