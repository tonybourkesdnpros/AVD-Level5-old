![Arista CVP Automation](https://img.shields.io/badge/Arista-CVP%20Automation-blue) ![Arista EOS Automation](https://img.shields.io/badge/Arista-EOS%20Automation-blue)

# AVD Arista Validated Design for Arista Level 5 Topology (DC1)

## About

This repository is configured to run [`arista.cvp`](https://github.com/aristanetworks/ansible-cvp) & [`arista.avd`](https://github.com/aristanetworks/ansible-avd) ansible collections against the Arista Level 5 lab Topology.

<p align="center">
  <img src='docs/imgs/cv_ansible_logo.png' alt='Arista CloudVision and Ansible'/>
</p>


## Lab Topology

The ATD Lab topology consists of two sets (DC1, DC2) of 3 Spines, 6 Leafs and 4 Hosts, as shown below.

<p align="center">
  <img src="docs/imgs/atd-topo.png" alt="ATD Lab Topology" width="600"/>
</p>

## ATD Topology Device List

| Device | IP Address   |
| ------ | ------------ |
| spine1-DC1 |192.168.0.11 |
| spine2-DC1 |192.168.0.12 |
| spine3-DC1 |192.168.0.13 |
| leaf1-DC1  |192.168.0.21 |
| leaf2-DC1  |192.168.0.22 |
| leaf3-DC1  |192.168.0.23 |
| leaf4-DC1  |192.168.0.24 |
| borderleaf1-DC1  |192.168.0.25 |
| borderleaf2-DC1  |192.168.0.26 |
| host1-DC1  |192.168.0.51 |
| host2-DC1  |192.168.0.52 |

Currently AVD for Level 5 works on only DC1

## Getting Started

Connect to your ATD Lab environment.   Once connected to the ATD Lab instance, select the Programmability IDE.  This container is built with all the necessary requirements and python modules to run AVD playbooks.


```shell
# Setup your git global config (optional)
git config --global user.email "you@example.com"
git config --global user.name "Your Name"

# Add arista.cvp, arista.avd, and update certain libraires
ansible-galaxy collection install arista.cvp
ansible-galaxy collection install arista.avd
pip install cvprac --upgrade

# Clone this repo
https://github.com/tonybourkesdnpros/AVD-Level5.git

# Move to directory
cd atd-avd

# Update Inventory with Lab Credentials
edit credentials in vscode: AVD-Level5/atd-inventory/inventory.yml

# Run Playbook to Prepare CloudVision for AVD
$ ansible-playbook playbooks/atd-prepare-lab.yml

# Execute Tasks in CVP manually

# Run Playbook to Deploy AVD Setup
$ ansible-playbook playbooks/atd-fabric-deploy.yml

# Execute Tasks in CVP manually

# Run audit playbook to validate Fabric states
$ ansible-playbook playbooks/atd-validate-states.yml

# Execute EOS_SNAPSHOT role to collect show commands
$ ansible-playbook playbooks/atd-snapshot.yml
```

## Step by Step walkthrough

A complete [step-by-step guide](./DEMO.md) is available

## Resources

- [Arista Ansible AVD Collection](https://github.com/aristanetworks/ansible-avd)
- [Arista Cloudvision Collection](https://github.com/aristanetworks/ansible-cvp)
- [Arista AVD public documentation](https://www.avd.sh)

## License

Project is published under [Apache License]().
