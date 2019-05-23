# ansible-role-vagrant

This role aims to install Vagrant, Vagrant plugins, and a desktop hypervisor. The supported platforms are:

  - MacOS
    + Currently reqires Homebrew
    + Homebrew installation of VirtualBox is currently broken (bottle bug)
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

    vagrant_install_fusion: true
    vagrant_fusion_key: "XXXXX-XXXXX-XXXXX-XXXXX-XXXXX"
    vagrant_default_provider: "vmare_desktop"

  roles:
    - ansible-role-vagrant
```

If you prefer, using ansible-vault to encrypt sensitive information works well:

```
vagrant_fusion_key: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          66393032343538396237356635326130623539303938656462333661666533613730316437646338
          6566616531383562626237356633343135633230646238380a323731386431633133313865663632
          32323666323536613831646639633138653137633563643964396365306335343136373331373130
          3161613265386334310a653430393766636665333761343562666665653061363765396464313937
          39323136336439343364333630363037396665653362636466623763376635396631
```

Also the entire license file could be encrypted with ansible-vault.


## History

This is the first role factored out of my macos-setup-ansible repo -- and my first shot at using Molecule (or anything really) to do automated testing of a role. So far, it's ugly but it works.
