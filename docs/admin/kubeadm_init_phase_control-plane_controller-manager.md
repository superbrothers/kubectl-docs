
Generates the kube-controller-manager static Pod manifest

```
kubeadm init phase control-plane controller-manager [flags]
```

### Options

```
      --cert-dir string             The path where to save and store the certificates. (default "/etc/kubernetes/pki")
      --config string               Path to a kubeadm configuration file.
      --dry-run                     Don't apply any changes; just output what would be done.
  -h, --help                        help for controller-manager
      --image-repository string     Choose a container registry to pull control plane images from (default "registry.k8s.io")
      --kubernetes-version string   Choose a specific Kubernetes version for the control plane. (default "stable-1")
      --patches string              Path to a directory that contains files named "target[suffix][+patchtype].extension". For example, "kube-apiserver0+merge.yaml" or just "etcd.json". "target" can be one of "kube-apiserver", "kube-controller-manager", "kube-scheduler", "etcd", "kubeletconfiguration", "corednsdeployment". "patchtype" can be one of "strategic", "merge" or "json" and they match the patch formats supported by kubectl. The default "patchtype" is "strategic". "extension" must be either "json" or "yaml". "suffix" is an optional string that can be used to determine which patches are applied first alpha-numerically.
      --pod-network-cidr string     Specify range of IP addresses for the pod network. If set, the control plane will automatically allocate CIDRs for every node.
```

### Options inherited from parent commands

```
      --rootfs string   The path to the 'real' host root filesystem. This will cause kubeadm to chroot into the provided path.
```
