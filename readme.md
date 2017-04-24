# Clean VM for CI workflow

This is a simple VagrantVM that can be used as the basis for a Continuous Integration workflow.

## Prerequisites

* vagrant

## Getting Started

Clone the project, navigate to the same directory as the vagrant file, and run `vagrant up`

## Notable features

* This VM uses the Bento/Ubuntu-16.04 base box
* There is 1 NIC
* An extra NIC is setup for connecting to the VM over a LAN
* Port 8001 on host forwards to 8000 on guest (for the python webserver)
* The shared folder is /vagrant
* /vagrant is owned by vagrant, in the group www-data
* vagrant is in the www-data group
* Permissions are 0777/0776, which is NOT SUITABLE FOR PRODUCTION
* 2 SSH keys are used:
  * the standard vagrant one
  * Another key, which can be generated and placed in keys/. It is also added to authorised_keys
* Password-based SSH is disabled
