# Verification and uninstalling Chaos Mesh

#### Verification

To verify the installation of chaos-mesh in previous step, execute

`kubectl get po -n chaos-mesh`{{execute}}

It should return the following output

```
NAME                                        READY   STATUS    RESTARTS   AGE
chaos-controller-manager-69fd5c46c8-xlqpc   3/3     Running   0          2d5h
chaos-daemon-jb8xh                          1/1     Running   0          2d5h
chaos-dashboard-98c4c5f97-tx5ds             1/1     Running   0          2d5h
```

#### version number

Additionally, to check the versions of kubernetes and Chaos Mesh installed, run the following commands,

`kubectl version`{{execute}} for kubernetes version, which returns

```
Client Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.0", GitCommit:"9e991415386e4cf155a24b1da15becaa390438d8", GitTreeState:"clean", BuildDate:"2020-03-25T14:58:59Z", GoVersion:"go1.13.8", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"18", GitVersion:"v1.18.0", GitCommit:"9e991415386e4cf155a24b1da15becaa390438d8", GitTreeState:"clean", BuildDate:"2020-03-25T14:50:46Z", GoVersion:"go1.13.8", Compiler:"gc", Platform:"linux/amd64"}
```

and

`helm list --namespace=chaos-mesh`{{execute}} for Chaos Mesh Version, which returns

```
NAME            NAMESPACE       REVISION        UPDATED                                STATUS   CHART                   APP VERSION
chaos-mesh      chaos-testing   1               2022-02-20 03:27:54.042876687 +0000 UTCdeployed chaos-mesh-2.1.3        2.1.3    
```

#### uninstall using helm

To uninstall Chaos Mesh using helm, simply run

`helm uninstall chaos-mesh -n chaos-mesh`{{execute}}
