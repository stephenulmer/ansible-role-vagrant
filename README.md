# ansible-role-vagrant

This role aims to install Vagrant and Vagrant plugins. Installation of the hypervisor has been moved into a separate role. The supported platforms are:

  - MacOS
    + Currently reqires Homebrew
  - Red Hat derivatives
    + Tested on CentOS


## Example Usage

```
---
- name: Install Vagrant
  hosts: all
  vars:
    vagrant_plugins:
      - vagrant-cachier
      - vagrant-hostmanager

    vagrant_plugins_licensed:
      - { name: "vagrant-vmware-desktop", licfile: "vagrant-license-Fusion11.lic" }

    vagrant_default_provider: "vmare_desktop"

  roles:
    - ansible-role-vagrant
```

Also the entire license file could be encrypted with ansible-vault.


## History

This is the first role factored out of my macos-setup-ansible repo -- and my first shot at using Molecule (or anything really) to do automated testing of a role. So far, it's ugly but it works.
