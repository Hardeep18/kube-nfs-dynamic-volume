# kube-nfs-dynamic-volume
nfs-provisioner

## Common Issue --> getting "unexpected error getting claim reference: selfLink was empty, can't make reference

```
Current workaround is to edit /etc/kubernetes/manifests/kube-apiserver.yaml

Under here:

spec:
  containers:
  - command:
    - kube-apiserver
Add this line:
- --feature-gates=RemoveSelfLink=false

The do this:
kubectl apply -f /etc/kubernetes/manifests/kube-apiserver.yaml
kubectl apply -f /etc/kubernetes/manifests/kube-apiserver.yaml

(I had to do it twice to get it to work)

```
