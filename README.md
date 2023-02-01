# vagrantExp
This is an experiment to document the vagrant files /configs needed to get a vm up and running.

Current repo should:
- provide a bare-bone Kubuntu working with virtualbox
- ssh /permission issues figured out
- make the process idempotent i.e. do vagrant up multiple times without worrying about changing insecure_key
- synched Documents folder for easy access from and to host machine (as Host-Document in the guest machine)
- enabled shared clipboard and drag and drop, for quickly begging your experiments

# Instructions

- First install virtualbox and vagrant
- Next cd into your favourite director and create a vm, for instance:
```
cd kubuntuExp/test1/
vagrant up
```


## Reference

Original Vagrant box cloud link: https://app.vagrantup.com/altafsaljooq/boxes/kubuntu22.04
