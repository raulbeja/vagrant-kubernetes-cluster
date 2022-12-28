# Vagrantfile and Scripts to Automate Kubernetes Cluster 

## Prerequisites

1. Vagrant Installed
[![Vagrant](https://img.shields.io/static/v1?message=Vagrant&logo=vagrant&labelColor=5c5c5c&color=1182c3&logoColor=white&label=%20&style=plastic)](https://developer.hashicorp.com/vagrant/downloads)
2. Virtualbox provider
[![VirtualBox](https://img.shields.io/static/v1?message=Virtualbox&logo=virtualbox&labelColor=5c5c5c&color=1182c3&logoColor=white&label=%20&style=plastic)](https://www.virtualbox.org/wiki/Downloads)
3. At least 4 cpus and 4Gb RAM workstation.

## Usage/Examples

To provision the cluster, execute the following commands.

```shell
git clone https://github.com/raulbeja/vagrant-kubernetes-cluster.git
cd vagrant-kubernetes-cluster
vagrant up --provider=virtualbox
```

## Automation Files ...

### Vagrantfile
```shell
Use nodes to map your cluster nodes configuration
nodes = [
    { :hostname => 'K8master',
      :ip => '192.168.56.20',
      :box => 'bento/ubuntu-20.04',
      :ram => 2048,
      :cpus => 2 }, 
    { :hostname => 'K8worker1',
      :ip => '192.168.56.51',
      :box => 'bento/ubuntu-20.04',
      :ram => 1024,
      :cpus => 1 }
  ]

Enabled hostmanager plugin to get hosts files updated.

```

### bootstrap.sh
```shell
Install docker community edition as container runtime and kubernetes tools in cluster nodes.

```
### master.sh
```shell
Install kubernetes components in master node.
Create shell script used by workers to join the cluster.

```

### worker.sh
```shell
Run joincluster.sh created by master.sh to join workers nodes to the cluster

```

## Basic Operations ...

### To connect to a cluster machine, 
```shell
vagrant ssh node[:hostname]

```

### To shutdown the cluster, 
```shell
vagrant halt

```

### To restart the cluster,
```shell
vagrant up

```

### To destroy the cluster, 
```shell
vagrant destroy -f

```