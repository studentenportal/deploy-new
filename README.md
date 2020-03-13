# deploy-new
New deployment setup, which is based on docker.

**NOTE: This repository is deprecated - see [deploy2020](https://github.com/studentenportal/deploy2020) for what's actually running on studentenportal.ch!**


# Infrastructure


> ---------   -------------------   ----------------
> | Proxy | - | studentenportal | - | postgres 9.6 |
> ---------   -------------------   ----------------


# Ansible

Automation of the deployment, recovery and backup operations. The
passwords are encrypted and stored in the key-file. The infrastructure
as code also serves as documentation.

## Ansible-Deploy

```bash
    ansible> ./ansible-run.sh
```

The script then asks for the name of the ansible script. The script
expects the file-name here without the extension.

```bash
    Name of script-file to execute:
    docker-service
```

Further ansible will ask for the `secrets.yaml` decryption password.
Afterwards ansible connects to the server and asks for the `ssh`
private-key decryption password.

When all secrets are correctly provided, the script will deploy the
playbook to the server.

## Ansible-Vault

Ansible-Vault manages protected ansible files. The file can be any type
of yaml files. We use it in this project as a variable file with the
passwords stored inside.
 
```bash
    ansible> ansible-vault edit secrets.yaml
```

To edit the encrypted file contents

```bash
    ansible> ansible-vault rekey secrets.yaml
```

Will change the secret password in order to hand the project to the next
maintainer group.

