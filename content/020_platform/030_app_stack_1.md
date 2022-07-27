+++
title = "F5XC App Stack"

weight = 30
+++

1. Check and see that our cluster is up an running.  
Below we should see our two K8s worker nodes:
```
kubectl get nodes
```
{{< output >}}     
NAME                                          STATUS   ROLES    AGE    VERSION
ip-10-0-3-204.eu-central-1.compute.internal   Ready    <none>   100s   v1.19.6-eks-49a6c0  
{{< /output >}}

2. Go to the lab directory

```
cd lab
```