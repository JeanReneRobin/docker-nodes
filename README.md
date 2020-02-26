# ansible-nodes
A shell script used to deploy and manage local docker containers for Ansible development.
Each container will be added into a local Ansible inventory.

```shell
ansible-nodes help
    
Description:
   A shell script used to deploy and manage local docker containers for Ansible development.
   Each container will be added into a local Ansible inventory.
 
Usage:
  ./ansible-nodes [command] [options]
    
Available Commands:
  help        		Dispaly this message
  pop [n] [i]      	Deploy n containers using i image. 25 nodes maximum. 
  download    		Download dockers images
  delete      		Delete containers
  stop        		Exit and clean existing environnement
```

### Example

Create 5 nodes : 
 
```shell
$ ansible-nodes pop 5 
[OK] - Nodes image downloaded
[OK] - Setting up network ansiblenodesnetwork
[OK] - Popped node1 - 10.0.101.10
[OK] - Deploying SSH key
[OK] - Popped node2 - 10.0.101.20
[OK] - Deploying SSH key
[OK] - Popped node3 - 10.0.101.30
[OK] - Deploying SSH key
[OK] - Popped node4 - 10.0.101.40
[OK] - Deploying SSH key
[OK] - Popped node5 - 10.0.101.50
[OK] - Deploying SSH key
```

Access the nodes using the ansible_nodes group : 

```shell
$ ansible -m ping ansible_nodes
node5 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
node1 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
node2 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
node3 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
node4 | SUCCESS => {
    "changed": false,
    "ping": "pong"
}

```
### Credits
https://github.com/Nani-o/ansible101
