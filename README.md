# Devstack Development

## Provisioning

Vagrant setup to provision openstack.

Prerequesites:
- virtual box
- ruby
- vagrant
- python/pip
- ansible
(OSX - ``sudo easy_install pip && sudo pip install ansible``)

How to:

```
cd provisioning
vagrant up (give it about 45 minutes to finish)
```

Once the script is finished, the output should look like that:

```
 This is your host ip: 10.0.2.15
==> default: 2015-06-25 17:12:06.861 | set lvm.conf device global_filter to: global_filter = [ "a|loop0|", "a|loop1|", "r|.*|" ] # from devstack
==> default: Horizon is now available at http://10.0.2.15/
==> default: Keystone is serving at http://10.0.2.15:5000/
==> default: The default users are: admin and demo
==> default: The password: pass
==> default: 2015-06-25 17:12:06.871 | stack.sh completed in 3526 seconds.
```

If you have a stronger computer you can double the amount of memory and cpus allocated to the VM in the VagrantFile. This will optimize installation and VM performance. Adjust the portion of the VagrantFile with the code below:

```
config.vm.provider :virtualbox do |vb|
   vb.customize ["modifyvm", :id, "--memory", "8192"]
   vb.customize ["modifyvm", :id, "--cpus", "4"]
 end
```

To open Horizon UI, go to http://192.168.50.4
