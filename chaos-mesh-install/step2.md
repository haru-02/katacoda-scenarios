# installing using helm.

Now, for production environment and other non-testing purposes, we can install Chaos Mesh using helm package manager.

To ensure helm is installed, run the following command.
`helm version`{{execute}}

It should return a similar output
```
version.BuildInfo{Version:"v3.5.4", GitCommit:"1b5edb69df3d3a08df77c9902dc17af864ff05d1", GitTreeState:"dirty", GoVersion: "go1.16.3"}
```
### step 1 : add chaos-mesh repository.

`helm repo add chaos-mesh https://charts.chaos-mesh.org`{{execute}}

### step 2 : view the installable versions of chaos-mesh.
 
 `helm search repo chaos-mesh`{{execute}}
 
The above command lists the latest version of chaos mesh. To list historical versions, run the following command.

`helm search repo chaos-mesh -l`{{execute}}

### step 3: create namespace to install workloads of Chaos Mesh

`kubectl create ns chaos-mesh`{{execute}}

### step 4: install chaos-mesh in different environments

Because socket paths are listened to by the daemons of different running containers, you need to set different values for socket paths during installation. You can execute the following installation commands according to different environments.

For this scenario, we will be using the command for docker environment. you can run the other commands depending on your local environment during a local installation.

#### Docker
`helm install chaos-mesh chaos-mesh/chaos-mesh -n=chaos-mesh --version 2.1.3`{{execute}}

#### Containered
```
helm install chaos-mesh chaos-mesh/chaos-mesh -n=chaos-testing --set chaosDaemon.runtime=containerd --set chaosDaemon.socketPath=/run/containerd/containerd.sock --version 2.1.3
```

#### K3S
```
helm install chaos-mesh chaos-mesh/chaos-mesh -n=chaos-testing --set chaosDaemon.runtime=containerd --set chaosDaemon.socketPath=/run/k3s/containerd/containerd.sock --version 2.1.3
```

#### CRI-O
```
helm install chaos-mesh chaos-mesh/chaos-mesh -n=chaos-testing --set chaosDaemon.runtime=crio --set chaosDaemon.socketPath=/var/run/crio/crio.sock --version 2.1.3
```

### Upgrade

To upgrade Chaos-Mesh, simply execute,

`helm upgrade chaos-mesh chaos-mesh/chaos-mesh`{{execute}}
