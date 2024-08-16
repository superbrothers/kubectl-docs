
Enable kubelet client certificate rotation

```
kubeadm init phase kubelet-finalize experimental-cert-rotation [flags]
```

### Options

```
      --cert-dir string   The path where to save and store the certificates. (default "/etc/kubernetes/pki")
      --config string     Path to a kubeadm configuration file.
      --dry-run           Don't apply any changes; just output what would be done.
  -h, --help              help for experimental-cert-rotation
```

### Options inherited from parent commands

```
      --rootfs string   [EXPERIMENTAL] The path to the 'real' host root filesystem.
```
