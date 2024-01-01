## Sample Playbooks to install K8s cluster

### Requirements
- Ubuntu 22.04
- hostname: "node-new"
- a user named "ansible" with ssh-key for passwordless auth pre-installed, and able to run sudo commands without password.
- a user for manual interaction on each host. 
- inventory.yml, copied from inventory.sample.yml and with the username of the manual user defined.

### Initialization
Deploy only one machine at a time. They should all be named "node-new" by the installer, and be automatically registered in DNS by DHCP.

For each new machine, run either of the playbooks "initNewMaster" or "initNewWorker". This will enumerate and set a permanent hostname, freeing up the name "node-new" for the next machine.

```command
 ansible-playbook -v initNewWorker.yml
 ```

This steps prepares each machine for management through ansible.

### Install K8s dependencies

The playbook "kube-dependencies" will add repositories to APT and install necessary software to create and run a k8s cluster.
```command
 ansible-playbook -v kube-dependencies.yml
 ```

### Create the cluster
The "master" playbook will initialize the cluster.
```command
 ansible-playbook -v master.yml
 ```

### Join the workers to the cluster
The "worker" playbook will join each worker machine to the already initialized cluster.
```command
 ansible-playbook -v workers.yml
 ```
