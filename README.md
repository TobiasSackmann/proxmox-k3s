# Proxmox-k3s

Terraform Repository for creating a Proxmox based virtual network.

Requirements
------------
* Terraform is installed on your target host
* Proxmox is installed on your target host
* Initial Proxmox configurations have been applied like creating an API Token
* An Cloud Init capable image is available on the Proxmox host. Within this repsoitory code it is called ubuntu2204-ci.
* An OVS Bridge with name vmbr10 with internet access is available on the Proxmox host.

Usage
-----
* After cloning this repository, you should update the modules with `git submodule update --init --recursive`
* Create your .tfvars file with the variables defined in the terraform/variables.tf
* Execute the setup.sh script from the setup direcory. It might be necessary to execute the fololowing steps manually, as sometimes the virtual machine is not directly ready after being created.
    * ```shell
        pushd ../k3s-ansible/
        ansible-playbook ./playbook/site.yml -i ../setup/inventory.yml
        popd 
        ```