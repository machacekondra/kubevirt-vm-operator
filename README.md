kubevirt-vm-operator
====================

Operator which deploy various operating systems on top of kubernetes.

# Installation
```bash
kubectl create -f deploy/crds/guest_v1alpha1_fedora29_crd.yaml
kubectl create -f deploy/service_account.yaml
kubectl create -f deploy/role.yaml
kubectl create -f deploy/role_binding.yaml
kubectl create -f deploy/operator.yaml
```

# Create Fedora29 virtual machine
```bash
$ cat deploy/crds/guest_v1alpha1_fedora29_cr.yaml
apiVersion: guest.kubevirt.io/v1alpha1
kind: Fedora29
metadata:
  name: myfedora29vm
spec:
  memory: 512Mi
  cpu_cores: 1
  namespace: default
  cloud_init:
    userData: |-
      #cloud-config
      password: fedora
      chpasswd: { expire: False }
```

Check it's created

```bash
kubectl get vm
```

# Troubleshooting

```bash
kubectl logs deploy/kubevirt-vm-oprator -c ansible
```
