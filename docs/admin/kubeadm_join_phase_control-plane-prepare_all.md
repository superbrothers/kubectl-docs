
Prepare the machine for serving a control plane

```
kubeadm join phase control-plane-prepare all [api-server-endpoint] [flags]
```

### Options

```
      --apiserver-advertise-address string            If the node should host a new control plane instance, the IP address the API Server will advertise it's listening on. If not set the default network interface will be used.
      --apiserver-bind-port int32                     If the node should host a new control plane instance, the port for the API Server to bind to. (default 6443)
      --certificate-key string                        Use this key to decrypt the certificate secrets uploaded by init. The certificate key is a hex encoded string that is an AES key of size 32 bytes.
      --config string                                 Path to a kubeadm configuration file.
      --control-plane                                 Create a new control plane instance on this node
      --discovery-file string                         For file-based discovery, a file or URL from which to load cluster information.
      --discovery-token string                        For token-based discovery, the token used to validate cluster information fetched from the API server.
      --discovery-token-ca-cert-hash strings          For token-based discovery, validate that the root CA public key matches this hash (format: "<type>:<value>").
      --discovery-token-unsafe-skip-ca-verification   For token-based discovery, allow joining without --discovery-token-ca-cert-hash pinning.
      --dry-run                                       Don't apply any changes; just output what would be done.
  -h, --help                                          help for all
      --node-name string                              Specify the node name.
      --patches string                                Path to a directory that contains files named "target[suffix][+patchtype].extension". For example, "kube-apiserver0+merge.yaml" or just "etcd.json". "target" can be one of "kube-apiserver", "kube-controller-manager", "kube-scheduler", "etcd", "kubeletconfiguration", "corednsdeployment". "patchtype" can be one of "strategic", "merge" or "json" and they match the patch formats supported by kubectl. The default "patchtype" is "strategic". "extension" must be either "json" or "yaml". "suffix" is an optional string that can be used to determine which patches are applied first alpha-numerically.
      --tls-bootstrap-token string                    Specify the token used to temporarily authenticate with the Kubernetes Control Plane while joining the node.
      --token string                                  Use this token for both discovery-token and tls-bootstrap-token when those values are not provided.
```

### Options inherited from parent commands

```
      --rootfs string   The path to the 'real' host root filesystem. This will cause kubeadm to chroot into the provided path.
```
