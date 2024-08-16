## kube-controller-manager



### Synopsis

The Kubernetes controller manager is a daemon that embeds
the core control loops shipped with Kubernetes. In applications of robotics and
automation, a control loop is a non-terminating loop that regulates the state of
the system. In Kubernetes, a controller is a control loop that watches the shared
state of the cluster through the apiserver and makes changes attempting to move the
current state towards the desired state. Examples of controllers that ship with
Kubernetes today are the replication controller, endpoints controller, namespace
controller, and serviceaccounts controller.

```
kube-controller-manager [flags]
```

### Options

```
      --allocate-node-cidrs                                            Should CIDRs for Pods be allocated and set on the cloud provider.
      --allow-metric-labels stringToString                             The map from metric-label to value allow-list of this label. The key's format is <MetricName>,<LabelName>. The value's format is <allowed_value>,<allowed_value>...e.g. metric1,label1='v1,v2,v3', metric1,label2='v1,v2,v3' metric2,label1='v1,v2,v3'. (default [])
      --allow-metric-labels-manifest string                            The path to the manifest file that contains the allow-list mapping. The format of the file is the same as the flag --allow-metric-labels. Note that the flag --allow-metric-labels will override the manifest file.
      --attach-detach-reconcile-sync-period duration                   The reconciler sync wait time between volume attach detach. This duration must be larger than one second, and increasing this value from the default may allow for volumes to be mismatched with pods. (default 1m0s)
      --authentication-kubeconfig string                               kubeconfig file pointing at the 'core' kubernetes server with enough rights to create tokenreviews.authentication.k8s.io. This is optional. If empty, all token requests are considered to be anonymous and no client CA is looked up in the cluster.
      --authentication-skip-lookup                                     If false, the authentication-kubeconfig will be used to lookup missing authentication configuration from the cluster.
      --authentication-token-webhook-cache-ttl duration                The duration to cache responses from the webhook token authenticator. (default 10s)
      --authentication-tolerate-lookup-failure                         If true, failures to look up missing authentication configuration from the cluster are not considered fatal. Note that this can result in authentication that treats all requests as anonymous.
      --authorization-always-allow-paths strings                       A list of HTTP paths to skip during authorization, i.e. these are authorized without contacting the 'core' kubernetes server. (default [/healthz,/readyz,/livez])
      --authorization-kubeconfig string                                kubeconfig file pointing at the 'core' kubernetes server with enough rights to create subjectaccessreviews.authorization.k8s.io. This is optional. If empty, all requests not skipped by authorization are forbidden.
      --authorization-webhook-cache-authorized-ttl duration            The duration to cache 'authorized' responses from the webhook authorizer. (default 10s)
      --authorization-webhook-cache-unauthorized-ttl duration          The duration to cache 'unauthorized' responses from the webhook authorizer. (default 10s)
      --bind-address ip                                                The IP address on which to listen for the --secure-port port. The associated interface(s) must be reachable by the rest of the cluster, and by CLI/web clients. If blank or an unspecified address (0.0.0.0 or ::), all interfaces and IP address families will be used. (default 0.0.0.0)
      --cert-dir string                                                The directory where the TLS certs are located. If --tls-cert-file and --tls-private-key-file are provided, this flag will be ignored.
      --cidr-allocator-type string                                     Type of CIDR allocator to use (default "RangeAllocator")
      --client-ca-file string                                          If set, any request presenting a client certificate signed by one of the authorities in the client-ca-file is authenticated with an identity corresponding to the CommonName of the client certificate.
      --cloud-config string                                            The path to the cloud provider configuration file. Empty string for no configuration file.
      --cloud-provider string                                          The provider for cloud services. Empty string for no provider.
      --cluster-cidr string                                            CIDR Range for Pods in cluster. Requires --allocate-node-cidrs to be true
      --cluster-name string                                            The instance prefix for the cluster. (default "kubernetes")
      --cluster-signing-cert-file string                               Filename containing a PEM-encoded X509 CA certificate used to issue cluster-scoped certificates.  If specified, no more specific --cluster-signing-* flag may be specified.
      --cluster-signing-duration duration                              The max length of duration signed certificates will be given.  Individual CSRs may request shorter certs by setting spec.expirationSeconds. (default 8760h0m0s)
      --cluster-signing-key-file string                                Filename containing a PEM-encoded RSA or ECDSA private key used to sign cluster-scoped certificates.  If specified, no more specific --cluster-signing-* flag may be specified.
      --cluster-signing-kube-apiserver-client-cert-file string         Filename containing a PEM-encoded X509 CA certificate used to issue certificates for the kubernetes.io/kube-apiserver-client signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-kube-apiserver-client-key-file string          Filename containing a PEM-encoded RSA or ECDSA private key used to sign certificates for the kubernetes.io/kube-apiserver-client signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-kubelet-client-cert-file string                Filename containing a PEM-encoded X509 CA certificate used to issue certificates for the kubernetes.io/kube-apiserver-client-kubelet signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-kubelet-client-key-file string                 Filename containing a PEM-encoded RSA or ECDSA private key used to sign certificates for the kubernetes.io/kube-apiserver-client-kubelet signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-kubelet-serving-cert-file string               Filename containing a PEM-encoded X509 CA certificate used to issue certificates for the kubernetes.io/kubelet-serving signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-kubelet-serving-key-file string                Filename containing a PEM-encoded RSA or ECDSA private key used to sign certificates for the kubernetes.io/kubelet-serving signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-legacy-unknown-cert-file string                Filename containing a PEM-encoded X509 CA certificate used to issue certificates for the kubernetes.io/legacy-unknown signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --cluster-signing-legacy-unknown-key-file string                 Filename containing a PEM-encoded RSA or ECDSA private key used to sign certificates for the kubernetes.io/legacy-unknown signer.  If specified, --cluster-signing-{cert,key}-file must not be set.
      --concurrent-cron-job-syncs int32                                The number of cron job objects that are allowed to sync concurrently. Larger number = more responsive jobs, but more CPU (and network) load (default 5)
      --concurrent-deployment-syncs int32                              The number of deployment objects that are allowed to sync concurrently. Larger number = more responsive deployments, but more CPU (and network) load (default 5)
      --concurrent-endpoint-syncs int32                                The number of endpoint syncing operations that will be done concurrently. Larger number = faster endpoint updating, but more CPU (and network) load (default 5)
      --concurrent-ephemeralvolume-syncs int32                         The number of ephemeral volume syncing operations that will be done concurrently. Larger number = faster ephemeral volume updating, but more CPU (and network) load (default 5)
      --concurrent-gc-syncs int32                                      The number of garbage collector workers that are allowed to sync concurrently. (default 20)
      --concurrent-horizontal-pod-autoscaler-syncs int32               The number of horizontal pod autoscaler objects that are allowed to sync concurrently. Larger number = more responsive horizontal pod autoscaler objects processing, but more CPU (and network) load. (default 5)
      --concurrent-job-syncs int32                                     The number of job objects that are allowed to sync concurrently. Larger number = more responsive jobs, but more CPU (and network) load (default 5)
      --concurrent-namespace-syncs int32                               The number of namespace objects that are allowed to sync concurrently. Larger number = more responsive namespace termination, but more CPU (and network) load (default 10)
      --concurrent-replicaset-syncs int32                              The number of replica sets that are allowed to sync concurrently. Larger number = more responsive replica management, but more CPU (and network) load (default 5)
      --concurrent-resource-quota-syncs int32                          The number of resource quotas that are allowed to sync concurrently. Larger number = more responsive quota management, but more CPU (and network) load (default 5)
      --concurrent-service-endpoint-syncs int32                        The number of service endpoint syncing operations that will be done concurrently. Larger number = faster endpoint slice updating, but more CPU (and network) load. Defaults to 5. (default 5)
      --concurrent-service-syncs int32                                 The number of services that are allowed to sync concurrently. Larger number = more responsive service management, but more CPU (and network) load (default 1)
      --concurrent-serviceaccount-token-syncs int32                    The number of service account token objects that are allowed to sync concurrently. Larger number = more responsive token generation, but more CPU (and network) load (default 5)
      --concurrent-statefulset-syncs int32                             The number of statefulset objects that are allowed to sync concurrently. Larger number = more responsive statefulsets, but more CPU (and network) load (default 5)
      --concurrent-ttl-after-finished-syncs int32                      The number of ttl-after-finished-controller workers that are allowed to sync concurrently. (default 5)
      --concurrent-validating-admission-policy-status-syncs int32      The number of ValidatingAdmissionPolicyStatusController workers that are allowed to sync concurrently. (default 5)
      --concurrent_rc_syncs int32                                      The number of replication controllers that are allowed to sync concurrently. Larger number = more responsive replica management, but more CPU (and network) load (default 5)
      --configure-cloud-routes                                         Should CIDRs allocated by allocate-node-cidrs be configured on the cloud provider. (default true)
      --contention-profiling                                           Enable block profiling, if profiling is enabled
      --controller-start-interval duration                             Interval between starting controller managers.
      --controllers strings                                            A list of controllers to enable. '*' enables all on-by-default controllers, 'foo' enables the controller named 'foo', '-foo' disables the controller named 'foo'.
                                                                       All controllers: bootstrap-signer-controller, certificatesigningrequest-approving-controller, certificatesigningrequest-cleaner-controller, certificatesigningrequest-signing-controller, cloud-node-lifecycle-controller, clusterrole-aggregation-controller, cronjob-controller, daemonset-controller, deployment-controller, disruption-controller, endpoints-controller, endpointslice-controller, endpointslice-mirroring-controller, ephemeral-volume-controller, garbage-collector-controller, horizontal-pod-autoscaler-controller, job-controller, legacy-serviceaccount-token-cleaner-controller, namespace-controller, node-ipam-controller, node-lifecycle-controller, node-route-controller, persistentvolume-attach-detach-controller, persistentvolume-binder-controller, persistentvolume-expander-controller, persistentvolume-protection-controller, persistentvolumeclaim-protection-controller, pod-garbage-collector-controller, replicaset-controller, replicationcontroller-controller, resourceclaim-controller, resourcequota-controller, root-ca-certificate-publisher-controller, service-cidr-controller, service-lb-controller, serviceaccount-controller, serviceaccount-token-controller, statefulset-controller, storage-version-migrator-controller, storageversion-garbage-collector-controller, taint-eviction-controller, token-cleaner-controller, ttl-after-finished-controller, ttl-controller, validatingadmissionpolicy-status-controller
                                                                       Disabled-by-default controllers: bootstrap-signer-controller, token-cleaner-controller (default [*])
      --disable-attach-detach-reconcile-sync                           Disable volume attach detach reconciler sync. Disabling this may cause volumes to be mismatched with pods. Use wisely.
      --disable-force-detach-on-timeout                                Prevent force detaching volumes based on maximum unmount time and node status. If this flag is set to true, the non-graceful node shutdown feature must be used to recover from node failure. See https://k8s.io/docs/storage-disable-force-detach-on-timeout/.
      --disabled-metrics strings                                       This flag provides an escape hatch for misbehaving metrics. You must provide the fully qualified metric name in order to disable it. Disclaimer: disabling metrics is higher in precedence than showing hidden metrics.
      --enable-dynamic-provisioning                                    Enable dynamic provisioning for environments that support it. (default true)
      --enable-garbage-collector                                       Enables the generic garbage collector. MUST be synced with the corresponding flag of the kube-apiserver. (default true)
      --enable-hostpath-provisioner                                    Enable HostPath PV provisioning when running without a cloud provider. This allows testing and development of provisioning features.  HostPath provisioning is not supported in any way, won't work in a multi-node cluster, and should not be used for anything other than testing or development.
      --enable-leader-migration                                        Whether to enable controller leader migration.
      --endpoint-updates-batch-period duration                         The length of endpoint updates batching period. Processing of pod changes will be delayed by this duration to join them with potential upcoming updates and reduce the overall number of endpoints updates. Larger number = higher endpoint programming latency, but lower number of endpoints revision generated
      --endpointslice-updates-batch-period duration                    The length of endpoint slice updates batching period. Processing of pod changes will be delayed by this duration to join them with potential upcoming updates and reduce the overall number of endpoints updates. Larger number = higher endpoint programming latency, but lower number of endpoints revision generated
      --external-cloud-volume-plugin string                            The plugin to use when cloud provider is set to external. Can be empty, should only be set when cloud-provider is external. Currently used to allow node-ipam-controller, persistentvolume-binder-controller, persistentvolume-expander-controller and attach-detach-controller to work for in tree cloud providers.
      --feature-gates mapStringBool                                    A set of key=value pairs that describe feature gates for alpha/experimental features. Options are:
                                                                       APIResponseCompression=true|false (BETA - default=true)
                                                                       APIServerIdentity=true|false (BETA - default=true)
                                                                       APIServerTracing=true|false (BETA - default=true)
                                                                       APIServingWithRoutine=true|false (BETA - default=true)
                                                                       AllAlpha=true|false (ALPHA - default=false)
                                                                       AllBeta=true|false (BETA - default=false)
                                                                       AnyVolumeDataSource=true|false (BETA - default=true)
                                                                       AppArmor=true|false (BETA - default=true)
                                                                       AppArmorFields=true|false (BETA - default=true)
                                                                       CPUManagerPolicyAlphaOptions=true|false (ALPHA - default=false)
                                                                       CPUManagerPolicyBetaOptions=true|false (BETA - default=true)
                                                                       CPUManagerPolicyOptions=true|false (BETA - default=true)
                                                                       CRDValidationRatcheting=true|false (BETA - default=true)
                                                                       CSIMigrationPortworx=true|false (BETA - default=false)
                                                                       CSIVolumeHealth=true|false (ALPHA - default=false)
                                                                       CloudControllerManagerWebhook=true|false (ALPHA - default=false)
                                                                       ClusterTrustBundle=true|false (ALPHA - default=false)
                                                                       ClusterTrustBundleProjection=true|false (ALPHA - default=false)
                                                                       ComponentSLIs=true|false (BETA - default=true)
                                                                       ConsistentListFromCache=true|false (ALPHA - default=false)
                                                                       ContainerCheckpoint=true|false (BETA - default=true)
                                                                       ContextualLogging=true|false (BETA - default=true)
                                                                       CronJobsScheduledAnnotation=true|false (BETA - default=true)
                                                                       CrossNamespaceVolumeDataSource=true|false (ALPHA - default=false)
                                                                       CustomCPUCFSQuotaPeriod=true|false (ALPHA - default=false)
                                                                       CustomResourceFieldSelectors=true|false (ALPHA - default=false)
                                                                       DevicePluginCDIDevices=true|false (BETA - default=true)
                                                                       DisableCloudProviders=true|false (BETA - default=true)
                                                                       DisableKubeletCloudCredentialProviders=true|false (BETA - default=true)
                                                                       DisableNodeKubeProxyVersion=true|false (ALPHA - default=false)
                                                                       DynamicResourceAllocation=true|false (ALPHA - default=false)
                                                                       ElasticIndexedJob=true|false (BETA - default=true)
                                                                       EventedPLEG=true|false (ALPHA - default=false)
                                                                       GracefulNodeShutdown=true|false (BETA - default=true)
                                                                       GracefulNodeShutdownBasedOnPodPriority=true|false (BETA - default=true)
                                                                       HPAScaleToZero=true|false (ALPHA - default=false)
                                                                       HonorPVReclaimPolicy=true|false (ALPHA - default=false)
                                                                       ImageMaximumGCAge=true|false (BETA - default=true)
                                                                       InPlacePodVerticalScaling=true|false (ALPHA - default=false)
                                                                       InTreePluginAWSUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginAzureDiskUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginAzureFileUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginGCEUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginOpenStackUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginPortworxUnregister=true|false (ALPHA - default=false)
                                                                       InTreePluginvSphereUnregister=true|false (ALPHA - default=false)
                                                                       InformerResourceVersion=true|false (ALPHA - default=false)
                                                                       JobBackoffLimitPerIndex=true|false (BETA - default=true)
                                                                       JobManagedBy=true|false (ALPHA - default=false)
                                                                       JobPodFailurePolicy=true|false (BETA - default=true)
                                                                       JobPodReplacementPolicy=true|false (BETA - default=true)
                                                                       JobSuccessPolicy=true|false (ALPHA - default=false)
                                                                       KubeProxyDrainingTerminatingNodes=true|false (BETA - default=true)
                                                                       KubeletCgroupDriverFromCRI=true|false (ALPHA - default=false)
                                                                       KubeletInUserNamespace=true|false (ALPHA - default=false)
                                                                       KubeletPodResourcesDynamicResources=true|false (ALPHA - default=false)
                                                                       KubeletPodResourcesGet=true|false (ALPHA - default=false)
                                                                       KubeletSeparateDiskGC=true|false (ALPHA - default=false)
                                                                       KubeletTracing=true|false (BETA - default=true)
                                                                       LoadBalancerIPMode=true|false (BETA - default=true)
                                                                       LocalStorageCapacityIsolationFSQuotaMonitoring=true|false (ALPHA - default=false)
                                                                       LogarithmicScaleDown=true|false (BETA - default=true)
                                                                       LoggingAlphaOptions=true|false (ALPHA - default=false)
                                                                       LoggingBetaOptions=true|false (BETA - default=true)
                                                                       MatchLabelKeysInPodAffinity=true|false (ALPHA - default=false)
                                                                       MatchLabelKeysInPodTopologySpread=true|false (BETA - default=true)
                                                                       MaxUnavailableStatefulSet=true|false (ALPHA - default=false)
                                                                       MemoryManager=true|false (BETA - default=true)
                                                                       MemoryQoS=true|false (ALPHA - default=false)
                                                                       MultiCIDRServiceAllocator=true|false (ALPHA - default=false)
                                                                       MutatingAdmissionPolicy=true|false (ALPHA - default=false)
                                                                       NFTablesProxyMode=true|false (ALPHA - default=false)
                                                                       NodeInclusionPolicyInPodTopologySpread=true|false (BETA - default=true)
                                                                       NodeLogQuery=true|false (BETA - default=false)
                                                                       NodeSwap=true|false (BETA - default=true)
                                                                       OpenAPIEnums=true|false (BETA - default=true)
                                                                       PDBUnhealthyPodEvictionPolicy=true|false (BETA - default=true)
                                                                       PersistentVolumeLastPhaseTransitionTime=true|false (BETA - default=true)
                                                                       PodAndContainerStatsFromCRI=true|false (ALPHA - default=false)
                                                                       PodDeletionCost=true|false (BETA - default=true)
                                                                       PodDisruptionConditions=true|false (BETA - default=true)
                                                                       PodIndexLabel=true|false (BETA - default=true)
                                                                       PodLifecycleSleepAction=true|false (BETA - default=true)
                                                                       PodReadyToStartContainersCondition=true|false (BETA - default=true)
                                                                       PortForwardWebsockets=true|false (ALPHA - default=false)
                                                                       ProcMountType=true|false (ALPHA - default=false)
                                                                       QOSReserved=true|false (ALPHA - default=false)
                                                                       RecoverVolumeExpansionFailure=true|false (ALPHA - default=false)
                                                                       RecursiveReadOnlyMounts=true|false (ALPHA - default=false)
                                                                       RelaxedEnvironmentVariableValidation=true|false (ALPHA - default=false)
                                                                       RetryGenerateName=true|false (ALPHA - default=false)
                                                                       RotateKubeletServerCertificate=true|false (BETA - default=true)
                                                                       RuntimeClassInImageCriApi=true|false (ALPHA - default=false)
                                                                       SELinuxMount=true|false (ALPHA - default=false)
                                                                       SELinuxMountReadWriteOncePod=true|false (BETA - default=true)
                                                                       SchedulerQueueingHints=true|false (BETA - default=false)
                                                                       SeparateCacheWatchRPC=true|false (BETA - default=true)
                                                                       SeparateTaintEvictionController=true|false (BETA - default=true)
                                                                       ServiceAccountTokenJTI=true|false (BETA - default=true)
                                                                       ServiceAccountTokenNodeBinding=true|false (ALPHA - default=false)
                                                                       ServiceAccountTokenNodeBindingValidation=true|false (BETA - default=true)
                                                                       ServiceAccountTokenPodNodeInfo=true|false (BETA - default=true)
                                                                       ServiceTrafficDistribution=true|false (ALPHA - default=false)
                                                                       SidecarContainers=true|false (BETA - default=true)
                                                                       SizeMemoryBackedVolumes=true|false (BETA - default=true)
                                                                       StatefulSetAutoDeletePVC=true|false (BETA - default=true)
                                                                       StatefulSetStartOrdinal=true|false (BETA - default=true)
                                                                       StorageNamespaceIndex=true|false (BETA - default=true)
                                                                       StorageVersionAPI=true|false (ALPHA - default=false)
                                                                       StorageVersionHash=true|false (BETA - default=true)
                                                                       StorageVersionMigrator=true|false (ALPHA - default=false)
                                                                       StructuredAuthenticationConfiguration=true|false (BETA - default=true)
                                                                       StructuredAuthorizationConfiguration=true|false (BETA - default=true)
                                                                       TopologyAwareHints=true|false (BETA - default=true)
                                                                       TopologyManagerPolicyAlphaOptions=true|false (ALPHA - default=false)
                                                                       TopologyManagerPolicyBetaOptions=true|false (BETA - default=true)
                                                                       TopologyManagerPolicyOptions=true|false (BETA - default=true)
                                                                       TranslateStreamCloseWebsocketRequests=true|false (BETA - default=true)
                                                                       UnauthenticatedHTTP2DOSMitigation=true|false (BETA - default=true)
                                                                       UnknownVersionInteroperabilityProxy=true|false (ALPHA - default=false)
                                                                       UserNamespacesPodSecurityStandards=true|false (ALPHA - default=false)
                                                                       UserNamespacesSupport=true|false (BETA - default=false)
                                                                       VolumeAttributesClass=true|false (ALPHA - default=false)
                                                                       VolumeCapacityPriority=true|false (ALPHA - default=false)
                                                                       WatchFromStorageWithoutResourceVersion=true|false (BETA - default=false)
                                                                       WatchList=true|false (ALPHA - default=false)
                                                                       WatchListClient=true|false (BETA - default=false)
                                                                       WinDSR=true|false (ALPHA - default=false)
                                                                       WinOverlay=true|false (BETA - default=true)
                                                                       WindowsHostNetwork=true|false (ALPHA - default=true)
      --flex-volume-plugin-dir string                                  Full path of the directory in which the flex volume plugin should search for additional third party volume plugins. (default "/usr/libexec/kubernetes/kubelet-plugins/volume/exec/")
  -h, --help                                                           help for kube-controller-manager
      --horizontal-pod-autoscaler-cpu-initialization-period duration   The period after pod start when CPU samples might be skipped. (default 5m0s)
      --horizontal-pod-autoscaler-downscale-stabilization duration     The period for which autoscaler will look backwards and not scale down below any recommendation it made during that period. (default 5m0s)
      --horizontal-pod-autoscaler-initial-readiness-delay duration     The period after pod start during which readiness changes will be treated as initial readiness. (default 30s)
      --horizontal-pod-autoscaler-sync-period duration                 The period for syncing the number of pods in horizontal pod autoscaler. (default 15s)
      --horizontal-pod-autoscaler-tolerance float                      The minimum change (from 1.0) in the desired-to-actual metrics ratio for the horizontal pod autoscaler to consider scaling. (default 0.1)
      --http2-max-streams-per-connection int                           The limit that the server gives to clients for the maximum number of streams in an HTTP/2 connection. Zero means to use golang's default.
      --kube-api-burst int32                                           Burst to use while talking with kubernetes apiserver. (default 30)
      --kube-api-content-type string                                   Content type of requests sent to apiserver. (default "application/vnd.kubernetes.protobuf")
      --kube-api-qps float32                                           QPS to use while talking with kubernetes apiserver. (default 20)
      --kubeconfig string                                              Path to kubeconfig file with authorization and master location information (the master location can be overridden by the master flag).
      --large-cluster-size-threshold int32                             Number of nodes from which node-lifecycle-controller treats the cluster as large for the eviction logic purposes. --secondary-node-eviction-rate is implicitly overridden to 0 for clusters this size or smaller. Notice: If nodes reside in multiple zones, this threshold will be considered as zone node size threshold for each zone to determine node eviction rate independently. (default 50)
      --leader-elect                                                   Start a leader election client and gain leadership before executing the main loop. Enable this when running replicated components for high availability. (default true)
      --leader-elect-lease-duration duration                           The duration that non-leader candidates will wait after observing a leadership renewal until attempting to acquire leadership of a led but unrenewed leader slot. This is effectively the maximum duration that a leader can be stopped before it is replaced by another candidate. This is only applicable if leader election is enabled. (default 15s)
      --leader-elect-renew-deadline duration                           The interval between attempts by the acting master to renew a leadership slot before it stops leading. This must be less than the lease duration. This is only applicable if leader election is enabled. (default 10s)
      --leader-elect-resource-lock string                              The type of resource object that is used for locking during leader election. Supported options are 'leases', 'endpointsleases' and 'configmapsleases'. (default "leases")
      --leader-elect-resource-name string                              The name of resource object that is used for locking during leader election. (default "kube-controller-manager")
      --leader-elect-resource-namespace string                         The namespace of resource object that is used for locking during leader election. (default "kube-system")
      --leader-elect-retry-period duration                             The duration the clients should wait between attempting acquisition and renewal of a leadership. This is only applicable if leader election is enabled. (default 2s)
      --leader-migration-config string                                 Path to the config file for controller leader migration, or empty to use the value that reflects default configuration of the controller manager. The config file should be of type LeaderMigrationConfiguration, group controllermanager.config.k8s.io, version v1alpha1.
      --legacy-service-account-token-clean-up-period duration          The period of time since the last usage of an legacy service account token before it can be deleted. (default 8760h0m0s)
      --log-flush-frequency duration                                   Maximum number of seconds between log flushes (default 5s)
      --log-text-info-buffer-size quantity                             [Alpha] In text format with split output streams, the info messages can be buffered for a while to increase performance. The default value of zero bytes disables buffering. The size can be specified as number of bytes (512), multiples of 1000 (1K), multiples of 1024 (2Ki), or powers of those (3M, 4G, 5Mi, 6Gi). Enable the LoggingAlphaOptions feature gate to use this.
      --log-text-split-stream                                          [Alpha] In text format, write error messages to stderr and info messages to stdout. The default is to write a single stream to stdout. Enable the LoggingAlphaOptions feature gate to use this.
      --logging-format string                                          Sets the log format. Permitted formats: "text". (default "text")
      --master string                                                  The address of the Kubernetes API server (overrides any value in kubeconfig).
      --max-endpoints-per-slice int32                                  The maximum number of endpoints that will be added to an EndpointSlice. More endpoints per slice will result in less endpoint slices, but larger resources. Defaults to 100. (default 100)
      --min-resync-period duration                                     The resync period in reflectors will be random between MinResyncPeriod and 2*MinResyncPeriod. (default 12h0m0s)
      --mirroring-concurrent-service-endpoint-syncs int32              The number of service endpoint syncing operations that will be done concurrently by the endpointslice-mirroring-controller. Larger number = faster endpoint slice updating, but more CPU (and network) load. Defaults to 5. (default 5)
      --mirroring-endpointslice-updates-batch-period duration          The length of EndpointSlice updates batching period for endpointslice-mirroring-controller. Processing of EndpointSlice changes will be delayed by this duration to join them with potential upcoming updates and reduce the overall number of EndpointSlice updates. Larger number = higher endpoint programming latency, but lower number of endpoints revision generated
      --mirroring-max-endpoints-per-subset int32                       The maximum number of endpoints that will be added to an EndpointSlice by the endpointslice-mirroring-controller. More endpoints per slice will result in less endpoint slices, but larger resources. Defaults to 100. (default 1000)
      --namespace-sync-period duration                                 The period for syncing namespace life-cycle updates (default 5m0s)
      --node-cidr-mask-size int32                                      Mask size for node cidr in cluster. Default is 24 for IPv4 and 64 for IPv6.
      --node-cidr-mask-size-ipv4 int32                                 Mask size for IPv4 node cidr in dual-stack cluster. Default is 24.
      --node-cidr-mask-size-ipv6 int32                                 Mask size for IPv6 node cidr in dual-stack cluster. Default is 64.
      --node-eviction-rate float32                                     Number of nodes per second on which pods are deleted in case of node failure when a zone is healthy (see --unhealthy-zone-threshold for definition of healthy/unhealthy). Zone refers to entire cluster in non-multizone clusters. (default 0.1)
      --node-monitor-grace-period duration                             Amount of time which we allow running Node to be unresponsive before marking it unhealthy. Must be N times more than kubelet's nodeStatusUpdateFrequency, where N means number of retries allowed for kubelet to post node status. (default 40s)
      --node-monitor-period duration                                   The period for syncing NodeStatus in cloud-node-lifecycle-controller. (default 5s)
      --node-startup-grace-period duration                             Amount of time which we allow starting Node to be unresponsive before marking it unhealthy. (default 1m0s)
      --permit-address-sharing                                         If true, SO_REUSEADDR will be used when binding the port. This allows binding to wildcard IPs like 0.0.0.0 and specific IPs in parallel, and it avoids waiting for the kernel to release sockets in TIME_WAIT state. [default=false]
      --permit-port-sharing                                            If true, SO_REUSEPORT will be used when binding the port, which allows more than one instance to bind on the same address and port. [default=false]
      --profiling                                                      Enable profiling via web interface host:port/debug/pprof/ (default true)
      --pv-recycler-increment-timeout-nfs int32                        the increment of time added per Gi to ActiveDeadlineSeconds for an NFS scrubber pod (default 30)
      --pv-recycler-minimum-timeout-hostpath int32                     The minimum ActiveDeadlineSeconds to use for a HostPath Recycler pod.  This is for development and testing only and will not work in a multi-node cluster. (default 60)
      --pv-recycler-minimum-timeout-nfs int32                          The minimum ActiveDeadlineSeconds to use for an NFS Recycler pod (default 300)
      --pv-recycler-pod-template-filepath-hostpath string              The file path to a pod definition used as a template for HostPath persistent volume recycling. This is for development and testing only and will not work in a multi-node cluster.
      --pv-recycler-pod-template-filepath-nfs string                   The file path to a pod definition used as a template for NFS persistent volume recycling
      --pv-recycler-timeout-increment-hostpath int32                   the increment of time added per Gi to ActiveDeadlineSeconds for a HostPath scrubber pod.  This is for development and testing only and will not work in a multi-node cluster. (default 30)
      --pvclaimbinder-sync-period duration                             The period for syncing persistent volumes and persistent volume claims (default 15s)
      --requestheader-allowed-names strings                            List of client certificate common names to allow to provide usernames in headers specified by --requestheader-username-headers. If empty, any client certificate validated by the authorities in --requestheader-client-ca-file is allowed.
      --requestheader-client-ca-file string                            Root certificate bundle to use to verify client certificates on incoming requests before trusting usernames in headers specified by --requestheader-username-headers. WARNING: generally do not depend on authorization being already done for incoming requests.
      --requestheader-extra-headers-prefix strings                     List of request header prefixes to inspect. X-Remote-Extra- is suggested. (default [x-remote-extra-])
      --requestheader-group-headers strings                            List of request headers to inspect for groups. X-Remote-Group is suggested. (default [x-remote-group])
      --requestheader-username-headers strings                         List of request headers to inspect for usernames. X-Remote-User is common. (default [x-remote-user])
      --resource-quota-sync-period duration                            The period for syncing quota usage status in the system (default 5m0s)
      --root-ca-file string                                            If set, this root certificate authority will be included in service account's token secret. This must be a valid PEM-encoded CA bundle.
      --route-reconciliation-period duration                           The period for reconciling routes created for Nodes by cloud provider. (default 10s)
      --secondary-node-eviction-rate float32                           Number of nodes per second on which pods are deleted in case of node failure when a zone is unhealthy (see --unhealthy-zone-threshold for definition of healthy/unhealthy). Zone refers to entire cluster in non-multizone clusters. This value is implicitly overridden to 0 if the cluster size is smaller than --large-cluster-size-threshold. (default 0.01)
      --secure-port int                                                The port on which to serve HTTPS with authentication and authorization. If 0, don't serve HTTPS at all. (default 10257)
      --service-account-private-key-file string                        Filename containing a PEM-encoded private RSA or ECDSA key used to sign service account tokens.
      --service-cluster-ip-range string                                CIDR Range for Services in cluster. Requires --allocate-node-cidrs to be true
      --show-hidden-metrics-for-version string                         The previous version for which you want to show hidden metrics. Only the previous minor version is meaningful, other values will not be allowed. The format is <major>.<minor>, e.g.: '1.16'. The purpose of this format is make sure you have the opportunity to notice if the next release hides additional metrics, rather than being surprised when they are permanently removed in the release after that.
      --terminated-pod-gc-threshold int32                              Number of terminated pods that can exist before the terminated pod garbage collector starts deleting terminated pods. If <= 0, the terminated pod garbage collector is disabled. (default 12500)
      --tls-cert-file string                                           File containing the default x509 Certificate for HTTPS. (CA cert, if any, concatenated after server cert). If HTTPS serving is enabled, and --tls-cert-file and --tls-private-key-file are not provided, a self-signed certificate and key are generated for the public address and saved to the directory specified by --cert-dir.
      --tls-cipher-suites strings                                      Comma-separated list of cipher suites for the server. If omitted, the default Go cipher suites will be used. 
                                                                       Preferred values: TLS_AES_128_GCM_SHA256, TLS_AES_256_GCM_SHA384, TLS_CHACHA20_POLY1305_SHA256, TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA, TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256, TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA, TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384, TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305, TLS_ECDHE_ECDSA_WITH_CHACHA20_POLY1305_SHA256, TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA, TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256, TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA, TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384, TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305, TLS_ECDHE_RSA_WITH_CHACHA20_POLY1305_SHA256. 
                                                                       Insecure values: TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256, TLS_ECDHE_ECDSA_WITH_RC4_128_SHA, TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA, TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256, TLS_ECDHE_RSA_WITH_RC4_128_SHA, TLS_RSA_WITH_3DES_EDE_CBC_SHA, TLS_RSA_WITH_AES_128_CBC_SHA, TLS_RSA_WITH_AES_128_CBC_SHA256, TLS_RSA_WITH_AES_128_GCM_SHA256, TLS_RSA_WITH_AES_256_CBC_SHA, TLS_RSA_WITH_AES_256_GCM_SHA384, TLS_RSA_WITH_RC4_128_SHA.
      --tls-min-version string                                         Minimum TLS version supported. Possible values: VersionTLS10, VersionTLS11, VersionTLS12, VersionTLS13
      --tls-private-key-file string                                    File containing the default x509 private key matching --tls-cert-file.
      --tls-sni-cert-key namedCertKey                                  A pair of x509 certificate and private key file paths, optionally suffixed with a list of domain patterns which are fully qualified domain names, possibly with prefixed wildcard segments. The domain patterns also allow IP addresses, but IPs should only be used if the apiserver has visibility to the IP address requested by a client. If no domain patterns are provided, the names of the certificate are extracted. Non-wildcard matches trump over wildcard matches, explicit domain patterns trump over extracted names. For multiple key/certificate pairs, use the --tls-sni-cert-key multiple times. Examples: "example.crt,example.key" or "foo.crt,foo.key:*.foo.com,foo.com". (default [])
      --unhealthy-zone-threshold float32                               Fraction of Nodes in a zone which needs to be not Ready (minimum 3) for zone to be treated as unhealthy.  (default 0.55)
      --use-service-account-credentials                                If true, use individual service account credentials for each controller.
  -v, --v Level                                                        number for the log level verbosity
      --version version[=true]                                         --version, --version=raw prints version information and quits; --version=vX.Y.Z... sets the reported version
      --vmodule pattern=N,...                                          comma-separated list of pattern=N settings for file-filtered logging (only works for text log format)
```
