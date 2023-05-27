## Inside the repository
![scripts_table](https://github.com/ShaanCoding/ReadME-Generator/assets/78090864/a55d60ed-21a6-468c-a4c0-977749297e53)

## Prerequisites

1. You should have a shh key (public and private), these will be used for communication between Buildbot, Builder and Client Virtual Machines.
  * You can use your existing key or,
  * You can generate a new one using: `ssh-keygen`
2. You should also have an public key, private key pair connected to github.
3. A user assigned managed identity, which has the role of Contributor assigned to it.
4. Two fileshares, one named test and one named scratch.

## Installation

1. Fill the parameters in config.yaml file (these include)
  * buildbot_vm_name: Name that you want to give to the buildbot virtual machine (**default value** : buildbotvm)
  * builder_vm_name: Name that you want to give to the builder virtual machine (**default value** : buildervm)
  * client_vm_name: Name that you want to give to the client virtual machine (**default value** : clientvm)
  * env_name: Name of the env you want to give (example v1), will be appended to the VM names
  * buildbot_sku: Size of the Buildbot Virtual Machine
  * builder_sku: Size of the Builder Virtual Machine (Should be enough to accomodate Kernel Build)
  * client_sku: Size of the Client Virtual Machine
  * image: the image of the Azure Virtual Machine to be used for builder,buildbot and client VMs
  * region: region in which the azure resources will be created
  * resource_group: Name of your resource group
  * subscription_id: Id of your azure subscription
  * mi_name: Name of the User Assigned Managed Identity
  * object_id_mi: Object Id of the User Assigned Managed Identity
  * client_id: Client id of the User Assigned Managed Identity
  * share_url_scratch: url of the share fileshare
  * share_url_test: url of the test fileshare
  * ssh_public_key_path: Path of your ssh public key to be used (example ~/.ssh/your_key.pub)
  * ssh_private_key_path: Path of your ssh private key to be used (example ~/.ssh/your_key)
  * github_ssh_publick_key_path: Path of your ssh public key associated to github (example ~/.ssh/your_key_github.pub)
  * github_ssh_private_key_path: Path of your ssh private key associated to github (example ~/.ssh/your_key_github)

2. Run the `smb-builbot-spinup.sh`
3. Open the url displayed after the spinup is complete
4. Trigger builds

## Usage
flag | functionality
--- | ---
 -i, --installation-scripts* | Run all installation scripts
 -c, --create-builder-vm | Run create-builder-vm script and subsequent setup scripts
 -s, --create-buildbot-vm  | Run create-buildbot-vm script and subsequent setup scripts
 -b, --setup-builder-vm | Run setup-builder-vm script and subsequent setup scripts
 -B, --setup-buildbot-vm  | Run only the setup-buildbot-vm script
 --help  | Show help information
