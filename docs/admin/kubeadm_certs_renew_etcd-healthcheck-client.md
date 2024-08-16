
Renew the certificate for liveness probes to healthcheck etcd

### Synopsis

Renew the certificate for liveness probes to healthcheck etcd.

Renewals run unconditionally, regardless of certificate expiration date; extra attributes such as SANs will be based on the existing file/certificates, there is no need to resupply them.

Renewal by default tries to use the certificate authority in the local PKI managed by kubeadm; as alternative it is possible to use K8s certificate API for certificate renewal, or as a last option, to generate a CSR request.

After renewal, in order to make changes effective, is required to restart control-plane components and eventually re-distribute the renewed certificate in case the file is used elsewhere.

```
kubeadm certs renew etcd-healthcheck-client [flags]
```

### Options

```
      --cert-dir string     The path where to save the certificates (default "/etc/kubernetes/pki")
      --config string       Path to a kubeadm configuration file.
  -h, --help                help for etcd-healthcheck-client
      --kubeconfig string   The kubeconfig file to use when talking to the cluster. If the flag is not set, a set of standard locations can be searched for an existing kubeconfig file. (default "/etc/kubernetes/admin.conf")
```

### Options inherited from parent commands

```
      --rootfs string   [EXPERIMENTAL] The path to the 'real' host root filesystem.
```
