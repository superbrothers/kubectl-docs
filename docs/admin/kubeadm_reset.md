
Performs a best effort revert of changes made to this host by 'kubeadm init' or 'kubeadm join'

### Synopsis

Performs a best effort revert of changes made to this host by 'kubeadm init' or 'kubeadm join'

The "reset" command executes the following phases:
```
preflight           Run reset pre-flight checks
remove-etcd-member  Remove a local etcd member.
cleanup-node        Run cleanup node.
```


```
kubeadm reset [flags]
```

### Options

```
      --cert-dir string                   The path to the directory where the certificates are stored. If specified, clean this directory. (default "/etc/kubernetes/pki")
      --cleanup-tmp-dir                   Cleanup the "/etc/kubernetes/tmp" directory
      --config string                     Path to a kubeadm configuration file.
      --cri-socket string                 Path to the CRI socket to connect. If empty kubeadm will try to auto-detect this value; use this option only if you have more than one CRI installed or if you have non-standard CRI socket.
      --dry-run                           Don't apply any changes; just output what would be done.
  -f, --force                             Reset the node without prompting for confirmation.
  -h, --help                              help for reset
      --ignore-preflight-errors strings   A list of checks whose errors will be shown as warnings. Example: 'IsPrivilegedUser,Swap'. Value 'all' ignores errors from all checks.
      --kubeconfig string                 The kubeconfig file to use when talking to the cluster. If the flag is not set, a set of standard locations can be searched for an existing kubeconfig file. (default "/etc/kubernetes/admin.conf")
      --skip-phases strings               List of phases to be skipped
```

### Options inherited from parent commands

```
      --rootfs string   [EXPERIMENTAL] The path to the 'real' host root filesystem.
```
