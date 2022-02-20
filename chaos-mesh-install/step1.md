# Setup and Quick install/uninstall.

To ensure that the kubernetes cluster is setup properly, run

`launch.sh`{{execute}}

in the terminal.

Now to install Chaos Mesh quickly for  only testing purposes,
run the following command in the terminal.

`curl -sSL https://mirrors.chaos-mesh.org/v2.1.3/install.sh | bash`{{execute}}

---
**Note**:

The current environment does not require you to add these flags, but if your local environment is "kind", add the following flag at the end of the above command.

`-s -- --local kind`

you can also add the following flag instead of the previous one if you would like to specify the kind version.

`-s -- --local kind --kind-version 0.10.0`

Instead, if your current local environment is k3s, add the `-s -- --k3s` flag.
similarly, for microk8s, the flag is `-s -- --microk8s`.

---

Running the command will quickly install chaos mesh into the environment for testing purposes. However, this is not recommended for production grade environment or for any non-testing purposes. For such use cases, it is strongly recommended to install using helm, which is discussed in the next section. 

To verify that Chaos Mesh is installed, run

`kubectl get po -n chaos-testing`{{execute}}

you should get an output similar to this,
```
NAME                                        READY   STATUS    RESTARTS  AGE
chaos-controller-manager-69fd5c46c8-xlqpc   3/3     Running   0         2d5h
chaos-daemon-jb8xh                          1/1     Running   0         2d5h
chaos-dashboard-98c4c5f97-tx5ds             1/1     Running   0         2d5h`
```
To uninstall Chaos Mesh, run the following command,

`curl -sSL https://mirrors.chaos-mesh.org/v2.1.3/install.sh | bash -s -- --template | kubectl delete -f -`{{execute}}

additionally, you can also delete the `chaos-testing` namespace to directly remove Chaos Mesh.

`kubectl delete ns chaos-testing`{{execute}}
