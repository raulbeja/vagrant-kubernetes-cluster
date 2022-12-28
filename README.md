# Vagrantfile and Scripts to Automate Kubernetes Cluster 

## Prerequisites

1. Vagrant Installed
2. At least 4 cpus and 4Gb RAM workstation.


## Usage/Examples

To provision the cluster, execute the following commands.

```shell
git clone https://github.com/raulbeja/vagrant-kubernetes-cluster.git
cd vagrant-kubernetes-cluster
vagrant up
```

## Vagrantfile

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

## bootstrap.sh
```shell
Install docker community editio as container runtime and kubernetes tools in cluster nodes.

```



## master.sh
```shell
Install kubernetes components in master node.
Create shell script used by workers to join the cluster.

```

## worker.sh
```shell
Run joincluster.sh created by master.sh to join worker to the cluster

```

## To connect to cluster machine, 

```shell
vagrant ssh node[:hostname]
```


## To shutdown the cluster, 

```shell
vagrant halt
```

## To restart the cluster,

```shell
vagrant up
```

## To destroy the cluster, 

```shell
vagrant destroy -f
```