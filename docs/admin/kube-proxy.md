## kube-proxy



### Synopsis

The Kubernetes network proxy runs on each node. This
reflects services as defined in the Kubernetes API on each node and can do simple
TCP, UDP, and SCTP stream forwarding or round robin TCP, UDP, and SCTP forwarding across a set of backends.
Service cluster IPs and ports are currently found through Docker-links-compatible
environment variables specifying ports opened by the service proxy. There is an optional
addon that provides cluster DNS for these cluster IPs. The user must create a service
with the apiserver API to configure the proxy.

```
kube-proxy [flags]
```

### Options

```
      --allow_dynamic_housekeeping                                 Whether to allow the housekeeping interval to be dynamic (default true)
      --application_metrics_count_limit int                        Max number of application metrics to store (per container) (default 100)
      --bind-address ip                                            Overrides kube-proxy's idea of what its node's primary IP is. Note that the name is a historical artifact, and kube-proxy does not actually bind any sockets to this IP. This parameter is ignored if a config file is specified by --config. (default 0.0.0.0)
      --bind-address-hard-fail                                     If true kube-proxy will treat failure to bind to a port as fatal and exit
      --boot_id_file string                                        Comma-separated list of files to check for boot-id. Use the first one that exists. (default "/proc/sys/kernel/random/boot_id")
      --cleanup                                                    If true cleanup iptables and ipvs rules and exit.
      --cloud-provider-gce-l7lb-src-cidrs cidrs                    CIDRs opened in GCE firewall for L7 LB traffic proxy & health checks (default 130.211.0.0/22,35.191.0.0/16)
      --cloud-provider-gce-lb-src-cidrs cidrs                      CIDRs opened in GCE firewall for L4 LB traffic proxy & health checks (default 130.211.0.0/22,209.85.152.0/22,209.85.204.0/22,35.191.0.0/16)
      --cluster-cidr string                                        The CIDR range of the pods in the cluster. (For dual-stack clusters, this can be a comma-separated dual-stack pair of CIDR ranges.). When --detect-local-mode is set to ClusterCIDR, kube-proxy will consider traffic to be local if its source IP is in this range. (Otherwise it is not used.) This parameter is ignored if a config file is specified by --config.
      --config string                                              The path to the configuration file.
      --config-sync-period duration                                How often configuration from the apiserver is refreshed.  Must be greater than 0. (default 15m0s)
      --conntrack-max-per-core int32                               Maximum number of NAT connections to track per CPU core (0 to leave the limit as-is and ignore conntrack-min). (default 32768)
      --conntrack-min int32                                        Minimum number of conntrack entries to allocate, regardless of conntrack-max-per-core (set conntrack-max-per-core=0 to leave the limit as-is). (default 131072)
      --conntrack-tcp-be-liberal                                   Enable liberal mode for tracking TCP packets by setting nf_conntrack_tcp_be_liberal to 1
      --conntrack-tcp-timeout-close-wait duration                  NAT timeout for TCP connections in the CLOSE_WAIT state (default 1h0m0s)
      --conntrack-tcp-timeout-established duration                 Idle timeout for established TCP connections (0 to leave as-is) (default 24h0m0s)
      --conntrack-udp-timeout duration                             Idle timeout for UNREPLIED UDP connections (0 to leave as-is)
      --conntrack-udp-timeout-stream duration                      Idle timeout for ASSURED UDP connections (0 to leave as-is)
      --container_hints string                                     location of the container hints file (default "/etc/cadvisor/container_hints.json")
      --containerd string                                          containerd endpoint (default "/run/containerd/containerd.sock")
      --containerd-namespace string                                containerd namespace (default "k8s.io")
      --containerd_env_metadata_whitelist env_metadata_whitelist   DEPRECATED: this flag will be removed, please use env_metadata_whitelist. A comma-separated list of environment variable keys matched with specified prefix that needs to be collected for containerd containers
      --crio_client_timeout duration                               CRI-O client timeout. Default is no timeout. (default 0s)
      --default-not-ready-toleration-seconds int                   Indicates the tolerationSeconds of the toleration for notReady:NoExecute that is added by default to every pod that does not already have such a toleration. (default 300)
      --default-unreachable-toleration-seconds int                 Indicates the tolerationSeconds of the toleration for unreachable:NoExecute that is added by default to every pod that does not already have such a toleration. (default 300)
      --detect-local-mode LocalMode                                Mode to use to detect local traffic. This parameter is ignored if a config file is specified by --config.
      --disable_root_cgroup_stats                                  Disable collecting root Cgroup stats
      --docker_only                                                Only report docker containers in addition to root stats
      --enable_load_reader                                         Whether to enable cpu load reader
      --event_storage_age_limit string                             Max length of time for which to store events (per type). Value is a comma separated list of key values, where the keys are event types (e.g.: creation, oom) or "default" and the value is a duration. Default is applied to all non-specified event types (default "default=0")
      --event_storage_event_limit string                           Max number of events to store (per type). Value is a comma separated list of key values, where the keys are event types (e.g.: creation, oom) or "default" and the value is an integer. Default is applied to all non-specified event types (default "default=0")
      --feature-gates mapStringBool                                A set of key=value pairs that describe feature gates for alpha/experimental features. Options are:
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
                                                                   This parameter is ignored if a config file is specified by --config.
      --global_housekeeping_interval duration                      Interval between global housekeepings (default 1m0s)
      --healthz-bind-address ipport                                The IP address and port for the health check server to serve on, defaulting to "0.0.0.0:10256" (if --bind-address is unset or IPv4), or "[::]:10256" (if --bind-address is IPv6). Set empty to disable. This parameter is ignored if a config file is specified by --config. (default 0.0.0.0:10256)
  -h, --help                                                       help for kube-proxy
      --hostname-override string                                   If non-empty, will be used as the name of the Node that kube-proxy is running on. If unset, the node name is assumed to be the same as the node's hostname.
      --housekeeping_interval duration                             Interval between container housekeepings (default 10s)
      --init-only                                                  If true, perform any initialization steps that must be done with full root privileges, and then exit. After doing this, you can run kube-proxy again with only the CAP_NET_ADMIN capability.
      --iptables-localhost-nodeports                               If false, kube-proxy will disable the legacy behavior of allowing NodePort services to be accessed via localhost. (Applies only to iptables mode and IPv4; localhost NodePorts are never allowed with other proxy modes or with IPv6.) (default true)
      --iptables-masquerade-bit int32                              If using the iptables or ipvs proxy mode, the bit of the fwmark space to mark packets requiring SNAT with.  Must be within the range [0, 31]. (default 14)
      --iptables-min-sync-period duration                          The minimum period between iptables rule resyncs (e.g. '5s', '1m', '2h22m'). A value of 0 means every Service or EndpointSlice change will result in an immediate iptables resync. (default 1s)
      --iptables-sync-period duration                              An interval (e.g. '5s', '1m', '2h22m') indicating how frequently various re-synchronizing and cleanup operations are performed. Must be greater than 0. (default 30s)
      --ipvs-exclude-cidrs strings                                 A comma-separated list of CIDRs which the ipvs proxier should not touch when cleaning up IPVS rules.
      --ipvs-min-sync-period duration                              The minimum period between IPVS rule resyncs (e.g. '5s', '1m', '2h22m'). A value of 0 means every Service or EndpointSlice change will result in an immediate IPVS resync.
      --ipvs-scheduler string                                      The ipvs scheduler type when proxy mode is ipvs
      --ipvs-strict-arp                                            Enable strict ARP by setting arp_ignore to 1 and arp_announce to 2
      --ipvs-sync-period duration                                  An interval (e.g. '5s', '1m', '2h22m') indicating how frequently various re-synchronizing and cleanup operations are performed. Must be greater than 0. (default 30s)
      --ipvs-tcp-timeout duration                                  The timeout for idle IPVS TCP connections, 0 to leave as-is. (e.g. '5s', '1m', '2h22m').
      --ipvs-tcpfin-timeout duration                               The timeout for IPVS TCP connections after receiving a FIN packet, 0 to leave as-is. (e.g. '5s', '1m', '2h22m').
      --ipvs-udp-timeout duration                                  The timeout for IPVS UDP packets, 0 to leave as-is. (e.g. '5s', '1m', '2h22m').
      --kube-api-burst int32                                       Burst to use while talking with kubernetes apiserver (default 10)
      --kube-api-content-type string                               Content type of requests sent to apiserver. (default "application/vnd.kubernetes.protobuf")
      --kube-api-qps float32                                       QPS to use while talking with kubernetes apiserver (default 5)
      --kubeconfig string                                          Path to kubeconfig file with authorization information (the master location can be overridden by the master flag).
      --log-flush-frequency duration                               Maximum number of seconds between log flushes (default 5s)
      --log-text-info-buffer-size quantity                         [Alpha] In text format with split output streams, the info messages can be buffered for a while to increase performance. The default value of zero bytes disables buffering. The size can be specified as number of bytes (512), multiples of 1000 (1K), multiples of 1024 (2Ki), or powers of those (3M, 4G, 5Mi, 6Gi). Enable the LoggingAlphaOptions feature gate to use this.
      --log-text-split-stream                                      [Alpha] In text format, write error messages to stderr and info messages to stdout. The default is to write a single stream to stdout. Enable the LoggingAlphaOptions feature gate to use this.
      --log_cadvisor_usage                                         Whether to log the usage of the cAdvisor container
      --logging-format string                                      Sets the log format. Permitted formats: "text". (default "text")
      --machine_id_file string                                     Comma-separated list of files to check for machine-id. Use the first one that exists. (default "/etc/machine-id,/var/lib/dbus/machine-id")
      --masquerade-all                                             If using the iptables or ipvs proxy mode, SNAT all traffic sent via Service cluster IPs. This may be required with some CNI plugins.
      --master string                                              The address of the Kubernetes API server (overrides any value in kubeconfig)
      --max_housekeeping_interval duration                         Largest interval to allow between container housekeepings (default 1m0s)
      --metrics-bind-address ipport                                The IP address and port for the metrics server to serve on, defaulting to "127.0.0.1:10249" (if --bind-address is unset or IPv4), or "[::1]:10249" (if --bind-address is IPv6). (Set to "0.0.0.0:10249" / "[::]:10249" to bind on all interfaces.) Set empty to disable. This parameter is ignored if a config file is specified by --config. (default 127.0.0.1:10249)
      --nodeport-addresses strings                                 A list of CIDR ranges that contain valid node IPs. If set, connections to NodePort services will only be accepted on node IPs in one of the indicated ranges. If unset, NodePort connections will be accepted on all local IPs. This parameter is ignored if a config file is specified by --config.
      --oom-score-adj int32                                        The oom-score-adj value for kube-proxy process. Values must be within the range [-1000, 1000]. This parameter is ignored if a config file is specified by --config. (default -999)
      --pod-bridge-interface string                                A bridge interface name. When --detect-local-mode is set to BridgeInterface, kube-proxy will consider traffic to be local if it originates from this bridge.
      --pod-interface-name-prefix string                           An interface name prefix. When --detect-local-mode is set to InterfaceNamePrefix, kube-proxy will consider traffic to be local if it originates from any interface whose name begins with this prefix.
      --profiling                                                  If true enables profiling via web interface on /debug/pprof handler. This parameter is ignored if a config file is specified by --config.
      --proxy-mode ProxyMode                                       Which proxy mode to use: on Linux this can be 'iptables' (default) or 'ipvs'. On Windows the only supported value is 'kernelspace'.This parameter is ignored if a config file is specified by --config.
      --referenced_reset_interval uint                             Reset interval for referenced bytes (container_referenced_bytes metric), number of measurement cycles after which referenced bytes are cleared, if set to 0 referenced bytes are never cleared (default: 0)
      --show-hidden-metrics-for-version string                     The previous version for which you want to show hidden metrics. Only the previous minor version is meaningful, other values will not be allowed. The format is <major>.<minor>, e.g.: '1.16'. The purpose of this format is make sure you have the opportunity to notice if the next release hides additional metrics, rather than being surprised when they are permanently removed in the release after that. This parameter is ignored if a config file is specified by --config.
      --storage_driver_buffer_duration duration                    Writes in the storage driver will be buffered for this duration, and committed to the non memory backends as a single transaction (default 1m0s)
      --storage_driver_db string                                   database name (default "cadvisor")
      --storage_driver_host string                                 database host:port (default "localhost:8086")
      --storage_driver_password string                             database password (default "root")
      --storage_driver_secure                                      use secure connection with database
      --storage_driver_table string                                table name (default "stats")
      --storage_driver_user string                                 database username (default "root")
      --update_machine_info_interval duration                      Interval between machine info updates. (default 5m0s)
  -v, --v Level                                                    number for the log level verbosity
      --version version[=true]                                     --version, --version=raw prints version information and quits; --version=vX.Y.Z... sets the reported version
      --vmodule pattern=N,...                                      comma-separated list of pattern=N settings for file-filtered logging (only works for text log format)
      --write-config-to string                                     If set, write the default configuration values to this file and exit.
```
