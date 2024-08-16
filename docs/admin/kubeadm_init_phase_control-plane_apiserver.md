
Generates the kube-apiserver static Pod manifest

```
kubeadm init phase control-plane apiserver [flags]
```

### Options

```
      --apiserver-advertise-address string     The IP address the API Server will advertise it's listening on. If not set the default network interface will be used.
      --apiserver-bind-port int32              Port for the API Server to bind to. (default 6443)
      --apiserver-extra-args mapStringString   A set of extra flags to pass to the API Server or override default ones in form of <flagname>=<value>
      --cert-dir string                        The path where to save and store the certificates. (default "/etc/kubernetes/pki")
      --config string                          Path to a kubeadm configuration file.
      --control-plane-endpoint string          Specify a stable IP address or DNS name for the control plane.
      --dry-run                                Don't apply any changes; just output what would be done.
      --feature-gates string                   A set of key=value pairs that describe feature gates for various features. Options are:
                                               EtcdLearnerMode=true|false (BETA - default=true)
                                               PublicKeysECDSA=true|false (DEPRECATED - default=false)
                                               RootlessControlPlane=true|false (ALPHA - default=false)
                                               UpgradeAddonsBeforeControlPlane=true|false (DEPRECATED - default=false)
                                               WaitForAllControlPlaneComponents=true|false (ALPHA - default=false)
  -h, --help                                   help for apiserver
      --image-repository string                Choose a container registry to pull control plane images from (default "registry.k8s.io")
      --kubernetes-version string              Choose a specific Kubernetes version for the control plane. (default "stable-1")
      --patches string                         Path to a directory that contains files named "target[suffix][+patchtype].extension". For example, "kube-apiserver0+merge.yaml" or just "etcd.json". "target" can be one of "kube-apiserver", "kube-controller-manager", "kube-scheduler", "etcd", "kubeletconfiguration". "patchtype" can be one of "strategic", "merge" or "json" and they match the patch formats supported by kubectl. The default "patchtype" is "strategic". "extension" must be either "json" or "yaml". "suffix" is an optional string that can be used to determine which patches are applied first alpha-numerically.
      --service-cidr string                    Use alternative range of IP address for service VIPs. (default "10.96.0.0/12")
```

### Options inherited from parent commands

```
      --rootfs string   [EXPERIMENTAL] The path to the 'real' host root filesystem.
```