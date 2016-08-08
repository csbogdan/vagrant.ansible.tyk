# vagrant.ansible.tyk
This repository is a simple Tyk deployer for Vagrant using Ansible.
It follows and enhances the instruction available @ https://tyk.io/docs/tyk-api-gateway-v-2-0/installation-options-setup/vagrant/ to automate as much as possible.

## OS Pre-Requisites
The following are required as pre-requisites

-   Brew
    This can be installed via `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

-   GIT

    This can be installed via `brew install git`

-   Vagrant

    This can be installed via `brew install vagrant`

-   VirtualBox

    This can be installed via `brew install virtualbox`

-   Ansible

    This can be installed via `brew install ansible`

-   Vagrant Plugins
    These can be installed via
    
    ```
    vagrant plugin install vagrant-hostmanager
    vagrant plugin install vagrant-vbguest
    ```

## Ansible Pre-Requisites
In order to deploy a license key is required for the product, which a 60 day free trial is available from https://tyk.io/tyk-professional-licenses/

-   Create the following directory within `vagrant.ansible.tyk`
	```
	git clone https://github.com/nirving-versent/vagrant.ansible.tyk.git
	cd vagrant.ansible.tyk
	mkdir -p group_vars\tyk\
	```

-   Create a file `common.yml` and provide the following details
    ```
    license_key: <LicenseKey>
    ```

# Deploy Tyk
Follow these steps to get a Tyk envvironment up and running. It uses the default values as per the instructions @  https://tyk.io/docs/tyk-api-gateway-v-2-0/installation-options-setup/vagrant/

-   Start the `vagrant up`  process
    ```
    cd vagrant.ansible.tyk
    vagrant up
    ```

-   Once completed the bootstrap details will be availabke @ `/opt/tyk-dashboard/logindetails.txt`
    ```
    vagrant ssh
    sudo -i
    more /opt/tyk-dashboard/logindetails.txt
    ```

-   If successful open a web browser to http://my-tyk-instance.com:3000/ and enter the details provided.

-   Follow the rest of the instructions 
    
    - [Set up and test your first API](https://tyk.io/docs/tyk-api-gateway-v-2-0/tutorials/set-up-your-first-api-pro-edition/)
    - [Set up your portal and publish your first API](https://tyk.io/docs/tyk-dashboard-v1-0/tutorials/set-up-your-portal/)