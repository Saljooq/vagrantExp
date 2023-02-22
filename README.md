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

## For adding a package.box directly

- download the *.box file
- let's say you want to call the distribution AarchExp"
```bash
vagrant box add ./package.box --name=AarchExp --force
```
- now we will AarchExp directly correspond to our local box
- we now cd into the directory with the vagrantfile and make sure name is consistent
- We will use our own private key in the folder and will not insert replacements to make it idempotent i.e. you should be able to get a completely fresh install in the same computer or even within this folder

```bash
Vagrant.configure("2") do |config|
  config.vm.box = "AarchExp"
  config.ssh.insert_key = false

   config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = true

    vb.name = "myAarchExperiment01"

    vb.customize ['modifyvm', :id, '--clipboard', 'bidirectional']

    vb.customize ['modifyvm', :id, '--drag-and-drop', 'bidirectional']

    config.ssh.private_key_path = "private_key"

  end
end
```


## Reference

Original Vagrant box cloud link: https://app.vagrantup.com/altafsaljooq/boxes/kubuntu22.04
