# ubuntu-minikube-vagrantfile

Just a simple Vagrantfile to deploy an Ubuntu 20.04.6 LTS (Focal Fossa) VM with minikube installed on it.

## How it works

To bring up and manage your VM, you will use [Vagrant](https://www.vagrantup.com/). So you have to install:

* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Vagrant](https://www.vagrantup.com/downloads.html)

Once you have installed [VirtualBox](https://www.virtualbox.org/) and [Vagrant](https://www.vagrantup.com/), just clone this repo and run:

```
vagrant up
```

you will create a VM with **4GB of RAM and 2 CPUs**, that has installed:

* [Ubuntu 20.04.6 LTS (Focal Fossa)](https://www.releases.ubuntu.com/focal/)
* [Docker Engine](https://docs.docker.com/engine/)
* [Minikube](https://minikube.sigs.k8s.io/docs/)

To access your brand new VM, just type

```
vagrant ssh
```

once you're connected, you can create a new minikube cluster just typing

```
minikube start
```

That creates a **single node minikube cluster**. To create other types of cluster, please review the [minikube documentation](https://minikube.sigs.k8s.io/docs/).

To control the cluster, minikube includes **kubectl**. For simplicity, an alias has been defined. You can use ```kubectl``` without prefix it with ```minikube```.

## Some considerations about the VM

* The vagrant box used is [ubuntu/focal64](https://app.vagrantup.com/ubuntu/boxes/focal64)
* Docker is installed following the [Docker official guide](https://docs.docker.com/engine/install/ubuntu/)
* Minikube is installed following the [Minikube official guide](https://minikube.sigs.k8s.io/docs/start/)
* No port is exposed as it is not considered neccesary for the use case. Feel free to change it modifying the Vagrantfile.
* You can change the amount of RAM and CPUs modifying these parameters in the Vagrantfile:
```
vbox.memory = 4096
vbox.cpus = 2
``` 

## Other useful vagrant commands

To stop the VM

```
vagrant halt
```

To destroy the VM

```
vagrant destroy
```

## License

MIT License

Copyright (c) 2023 danuser2018

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
