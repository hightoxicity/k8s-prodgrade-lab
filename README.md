# k8s-prodgrade-lab: Network Automation Lab around K8S + Vyos spine-leaf architecture

Aim of the project is to create a kubernetes cluster self-contained into a local environment (one more).

Advantage of the solution is to reproduce locally a production grade networking.

The project main focus is to use the same project for both vagrant and production env provisioning.

This lab creates a simple spine-leaf architecture with vyos virtual machines.

You will have:
* One vyos spine
* Two vyos leaves
* A k8s master node and a worker node under the first leaf
* Another worker node under the second leaf
* A NAT output gateway
* A provisioner (isc-dhcp-server, tftp, nginx webserver, traffic server http/https proxy)

The lab is based on the following software:
* Vyos
* Vagrant
* VirtualBox/Libvirt
* Ansible
* Kubernetes
* Calico
* Packer
* Coreos Linux Container
* Apache Traffic Server

The network design is a basic leaf/spine topology (AS per rack model) that will be built using eBGP peerings.

The K8S network SDN is a calico full l3 solution ensuring pod networking.

## Network design:

![alt text](https://github.com/hightoxicity/k8s-prodgrade-lab/raw/master/doc/infra_diagram.png "Network Design")

## Build it:

At root of the projet, run:

```bash
make
```

## Use it:

```bash
vagrant up --provider virtualbox
vagrant ssh provisioner -- -t 'cd /provisioning; ansible-playbook site.yml'
```

## Think it (work in progress/features to come):

* Hardware discovery (ipmi, mac addresses) and ansible inventory generation
* Libvirt support with ipxe boot
