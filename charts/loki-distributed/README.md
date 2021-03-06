# loki-distributed

![Version: 0.13.0](https://img.shields.io/badge/Version-0.13.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 2.0.0](https://img.shields.io/badge/AppVersion-2.0.0-informational?style=flat-square)

Helm chart for Grafana Loki in microservices mode

**Homepage:** <https://github.com/unguiculus/loki-helm-chart>

## Source Code

* <https://github.com/grafana/loki>
* <https://grafana.com/oss/loki/>
* <https://grafana.com/docs/loki/latest/>

## Chart Repo

Add the following repo to use the chart:

```console
helm repo add loki https://unguiculus.github.io/loki-helm-chart
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| compactor.enabled | bool | `false` | Specifies whether compactor should be enabled |
| compactor.extraArgs | list | `[]` | Additional CLI args for the compactor |
| compactor.extraEnv | list | `[]` | Environment variables to add to the compactor pods |
| compactor.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the compactor pods |
| compactor.image.registry | string | `nil` | The Docker registry for the compactor image. Overrides `loki.image.registry` |
| compactor.image.repository | string | `nil` | Docker image repository for the compactor image. Overrides `loki.image.repository` |
| compactor.image.tag | string | `nil` | Docker image tag for the compactor image. Overrides `loki.image.tag` |
| compactor.nodeSelector | object | `{}` | Node selector for compactor pods |
| compactor.persistence.enabled | bool | `false` | Enable creating PVCs for the compactor |
| compactor.persistence.size | string | `"10Gi"` | Size of persistent disk |
| compactor.persistence.storageClass | string | `nil` | Storage class to be used. If defined, storageClassName: <storageClass>. If set to "-", storageClassName: "", which disables dynamic provisioning. If empty or set to null, no storageClassName spec is set, choosing the default provisioner (gp2 on AWS, standard on GKE, AWS, and OpenStack). |
| compactor.podAnnotations | object | `{}` | Annotations for compactor pods |
| compactor.resources | object | `{}` | Resource requests and limits for the compactor |
| compactor.terminationGracePeriodSeconds | int | `30` | Grace period to allow the compactor to shutdown before it is killed |
| compactor.tolerations | list | `[]` | Tolerations for compactor pods |
| distributor.affinity | string | Hard node and soft zone anti-affinity | Affinity for distributor pods. Passed through `tpl` and, thus, to be configured as string |
| distributor.extraArgs | list | `[]` | Additional CLI args for the distributor |
| distributor.extraEnv | list | `[]` | Environment variables to add to the distributor pods |
| distributor.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the distributor pods |
| distributor.image.registry | string | `nil` | The Docker registry for the distributor image. Overrides `loki.image.registry` |
| distributor.image.repository | string | `nil` | Docker image repository for the distributor image. Overrides `loki.image.repository` |
| distributor.image.tag | string | `nil` | Docker image tag for the distributor image. Overrides `loki.image.tag` |
| distributor.nodeSelector | object | `{}` | Node selector for distributor pods |
| distributor.podAnnotations | object | `{}` | Annotations for distributor pods |
| distributor.replicas | int | `1` | Number of replicas for the distributor |
| distributor.resources | object | `{}` | Resource requests and limits for the distributor |
| distributor.terminationGracePeriodSeconds | int | `30` | Grace period to allow the distributor to shutdown before it is killed |
| distributor.tolerations | list | `[]` | Tolerations for distributor pods |
| fullnameOverride | string | `nil` | Overrides the chart's computed fullname |
| gateway.affinity | string | Hard node and soft zone anti-affinity | Affinity for gateway pods. Passed through `tpl` and, thus, to be configured as string |
| gateway.basicAuth.enabled | bool | `false` | Enables basic authentication for the gateway |
| gateway.basicAuth.existingSecret | string | `nil` | Existing basic auth secret to use. Must contain '.htpasswd' |
| gateway.basicAuth.password | string | `nil` | The basic auth password for the gateway |
| gateway.basicAuth.username | string | `nil` | The basic auth username for the gateway |
| gateway.extraArgs | list | `[]` | Additional CLI args for the gateway |
| gateway.extraEnv | list | `[]` | Environment variables to add to the gateway pods |
| gateway.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the gateway pods |
| gateway.image.pullPolicy | string | `"IfNotPresent"` | The gateway image pull policy |
| gateway.image.registry | string | `"docker.io"` | The Docker registry for the gateway image |
| gateway.image.repository | string | `"nginxinc/nginx-unprivileged"` | The gateway image repository |
| gateway.image.tag | string | `"1.19-alpine"` | The gateway image tag |
| gateway.ingress.annotations | object | `{}` | Annotations for the gateway ingress |
| gateway.ingress.enabled | bool | `false` | Specifies whether an ingress for the gateway should be created |
| gateway.ingress.hosts | list | `[{"host":"gateway.loki.example.com","paths":["/"]}]` | Hosts configuration for the gateway ingress |
| gateway.ingress.tls | list | `[{"hosts":["gateway.loki.example.com"],"secretName":"loki-gateway-tls"}]` | TLS configuration for the gateway ingress |
| gateway.nginxConfig | string | See values.yaml | Config file contents for Nginx. Passed through the `tpl` function to allow templating |
| gateway.nodeSelector | object | `{}` | Node selector for gateway pods |
| gateway.podAnnotations | object | `{}` | Annotations for gateway pods |
| gateway.replicas | int | `1` | Number of replicas for the gateway |
| gateway.resources | object | `{}` | Resource requests and limits for the gateway |
| gateway.service.clusterIP | string | `nil` | ClusterIP of the gateway service |
| gateway.service.loadBalancerIP | string | `nil` | Load balancer IPO address if service type is LoadBalancer |
| gateway.service.nodePort | string | `nil` | Node port if service type is NodePort |
| gateway.service.port | int | `80` | Port of the gateway service |
| gateway.service.type | string | `"ClusterIP"` | Type of the gateway service |
| gateway.terminationGracePeriodSeconds | int | `30` | Grace period to allow the gateway to shutdown before it is killed |
| gateway.tolerations | list | `[]` | Tolerations for gateway pods |
| global.image.registry | string | `nil` | Overrides the Docker registry globally for all images |
| imagePullSecrets | list | `[]` | Image pull secrets for Docker images |
| ingester.affinity | string | Hard node and soft zone anti-affinity | Affinity for ingester pods. Passed through `tpl` and, thus, to be configured as string |
| ingester.extraArgs | list | `[]` | Additional CLI args for the ingester |
| ingester.extraEnv | list | `[]` | Environment variables to add to the ingester pods |
| ingester.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the ingester pods |
| ingester.image.registry | string | `nil` | The Docker registry for the ingester image. Overrides `loki.image.registry` |
| ingester.image.repository | string | `nil` | Docker image repository for the ingester image. Overrides `loki.image.repository` |
| ingester.image.tag | string | `nil` | Docker image tag for the ingester image. Overrides `loki.image.tag` |
| ingester.nodeSelector | object | `{}` | Node selector for ingester pods |
| ingester.persistence.enabled | bool | `false` | Enable creating PVCs which is required when using boltdb-shipper |
| ingester.persistence.size | string | `"10Gi"` | Size of persistent disk |
| ingester.persistence.storageClass | string | `nil` | Storage class to be used. If defined, storageClassName: <storageClass>. If set to "-", storageClassName: "", which disables dynamic provisioning. If empty or set to null, no storageClassName spec is set, choosing the default provisioner (gp2 on AWS, standard on GKE, AWS, and OpenStack). |
| ingester.podAnnotations | object | `{}` | Annotations for ingester pods |
| ingester.replicas | int | `2` | Number of replicas for the ingester |
| ingester.resources | object | `{}` | Resource requests and limits for the ingester |
| ingester.terminationGracePeriodSeconds | int | `300` | Grace period to allow the ingester to shutdown before it is killed. Especially for the ingestor, this must be increased. It must be long enough so ingesters can be gracefully shutdown flushing/transferring all data and to successfully leave the member ring on shutdown. |
| ingester.tolerations | list | `[]` | Tolerations for ingester pods |
| loki.config | string | See values.yaml | Config file contents for Loki |
| loki.image.pullPolicy | string | `"IfNotPresent"` | Docker image pull policy |
| loki.image.registry | string | `"docker.io"` | The Docker registry |
| loki.image.repository | string | `"grafana/loki"` | Docker image repository |
| loki.image.tag | string | `nil` | Overrides the image tag whose default is the chart's appVersion |
| loki.memberlist | bool | `true` | If true, an additional headless service for memberlist (including ingester, distributor, and quierier pods) is created |
| loki.podAnnotations | object | `{}` | Common annotations for all pods |
| loki.revisionHistoryLimit | int | `10` | The number of old ReplicaSets to retain to allow rollback |
| memcached.image.pullPolicy | string | `"IfNotPresent"` | Memcached Docker image pull policy |
| memcached.image.registry | string | `"docker.io"` | The Docker registry for the memcached |
| memcached.image.repository | string | `"memcached"` | Memcached Docker image repository |
| memcached.image.tag | string | `"1.6.7-alpine"` | Memcached Docker image tag |
| memcachedChunks.affinity | string | Hard node and soft zone anti-affinity | Affinity for memcached-chunks pods. Passed through `tpl` and, thus, to be configured as string |
| memcachedChunks.enabled | bool | `false` | Specifies whether the Memcached chunks cache should be enabled |
| memcachedChunks.extraArgs | list | `[]` | Additional CLI args for memcached-chunks |
| memcachedChunks.extraEnv | list | `[]` | Environment variables to add to memcached-chunks pods |
| memcachedChunks.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to memcached-chunks pods |
| memcachedChunks.nodeSelector | object | `{}` | Node selector for memcached-chunks pods |
| memcachedChunks.podAnnotations | object | `{}` | Annotations for memcached-chunks pods |
| memcachedChunks.replicas | int | `1` | Number of replicas for memcached-chunks |
| memcachedChunks.resources | object | `{}` | Resource requests and limits for memcached-chunks |
| memcachedChunks.terminationGracePeriodSeconds | int | `30` | Grace period to allow memcached-chunks to shutdown before it is killed |
| memcachedChunks.tolerations | list | `[]` | Tolerations for memcached-chunks pods |
| memcachedExporter.enabled | bool | `false` | Specifies whether the Memcached Exporter should be enabled |
| memcachedExporter.image.pullPolicy | string | `"IfNotPresent"` | Memcached Exporter Docker image pull policy |
| memcachedExporter.image.registry | string | `"docker.io"` | The Docker registry for the Memcached Exporter |
| memcachedExporter.image.repository | string | `"prom/memcached-exporter"` | Memcached Exporter Docker image repository |
| memcachedExporter.image.tag | string | `"v0.6.0"` | Memcached Exporter Docker image tag |
| memcachedFrontend.affinity | string | Hard node and soft zone anti-affinity | Affinity for memcached-frontend pods. Passed through `tpl` and, thus, to be configured as string |
| memcachedFrontend.enabled | bool | `false` | Specifies whether the Memcached frontend cache should be enabled |
| memcachedFrontend.extraArgs | list | `[]` | Additional CLI args for memcached-frontend |
| memcachedFrontend.extraEnv | list | `[]` | Environment variables to add to memcached-frontend pods |
| memcachedFrontend.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to memcached-frontend pods |
| memcachedFrontend.nodeSelector | object | `{}` | Node selector for memcached-frontend pods |
| memcachedFrontend.podAnnotations | object | `{}` | Annotations for memcached-frontend pods |
| memcachedFrontend.replicas | int | `1` | Number of replicas for memcached-frontend |
| memcachedFrontend.resources | object | `{}` | Resource requests and limits for memcached-frontend |
| memcachedFrontend.terminationGracePeriodSeconds | int | `30` | Grace period to allow memcached-frontend to shutdown before it is killed |
| memcachedFrontend.tolerations | list | `[]` | Tolerations for memcached-frontend pods |
| memcachedIndexQueries.affinity | string | Hard node and soft zone anti-affinity | Affinity for memcached-index-queries pods. Passed through `tpl` and, thus, to be configured as string |
| memcachedIndexQueries.enabled | bool | `false` | Specifies whether the Memcached index queries cache should be enabled |
| memcachedIndexQueries.extraArgs | list | `[]` | Additional CLI args for memcached-index-queries |
| memcachedIndexQueries.extraEnv | list | `[]` | Environment variables to add to memcached-index-queries pods |
| memcachedIndexQueries.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to memcached-index-queries pods |
| memcachedIndexQueries.nodeSelector | object | `{}` | Node selector for memcached-index-queries pods |
| memcachedIndexQueries.podAnnotations | object | `{}` | Annotations for memcached-index-queries pods |
| memcachedIndexQueries.replicas | int | `1` | Number of replicas for memcached-index-queries |
| memcachedIndexQueries.resources | object | `{}` | Resource requests and limits for memcached-index-queries |
| memcachedIndexQueries.terminationGracePeriodSeconds | int | `30` | Grace period to allow memcached-index-queries to shutdown before it is killed |
| memcachedIndexQueries.tolerations | list | `[]` | Tolerations for memcached-index-queries pods |
| memcachedIndexWrites.affinity | string | Hard node and soft zone anti-affinity | Affinity for memcached-index-writes pods. Passed through `tpl` and, thus, to be configured as string |
| memcachedIndexWrites.enabled | bool | `false` | Specifies whether the Memcached index writes cache should be enabled |
| memcachedIndexWrites.extraArgs | list | `[]` | Additional CLI args for memcached-index-writes |
| memcachedIndexWrites.extraEnv | list | `[]` | Environment variables to add to memcached-index-writes pods |
| memcachedIndexWrites.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to memcached-index-writes pods |
| memcachedIndexWrites.nodeSelector | object | `{}` | Node selector for memcached-index-writes pods |
| memcachedIndexWrites.podAnnotations | object | `{}` | Annotations for memcached-index-writes pods |
| memcachedIndexWrites.replicas | int | `1` | Number of replicas for memcached-index-writes |
| memcachedIndexWrites.resources | object | `{}` | Resource requests and limits for memcached-index-writes |
| memcachedIndexWrites.terminationGracePeriodSeconds | int | `30` | Grace period to allow memcached-index-writes to shutdown before it is killed |
| memcachedIndexWrites.tolerations | list | `[]` | Tolerations for memcached-index-writes pods |
| nameOverride | string | `nil` | Overrides the chart's name |
| querier.affinity | string | Hard node and soft zone anti-affinity | Affinity for querier pods. Passed through `tpl` and, thus, to be configured as string |
| querier.extraArgs | list | `[]` | Additional CLI args for the querier |
| querier.extraEnv | list | `[]` | Environment variables to add to the querier pods |
| querier.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the querier pods |
| querier.image.registry | string | `nil` | The Docker registry for the querier image. Overrides `loki.image.registry` |
| querier.image.repository | string | `nil` | Docker image repository for the querier image. Overrides `loki.image.repository` |
| querier.image.tag | string | `nil` | Docker image tag for the querier image. Overrides `loki.image.tag` |
| querier.nodeSelector | object | `{}` | Node selector for querier pods |
| querier.persistence.enabled | bool | `false` | Enable creating PVCs for the querier cache |
| querier.persistence.size | string | `"10Gi"` | Size of persistent disk |
| querier.persistence.storageClass | string | `nil` | Storage class to be used. If defined, storageClassName: <storageClass>. If set to "-", storageClassName: "", which disables dynamic provisioning. If empty or set to null, no storageClassName spec is set, choosing the default provisioner (gp2 on AWS, standard on GKE, AWS, and OpenStack). |
| querier.podAnnotations | object | `{}` | Annotations for querier pods |
| querier.replicas | int | `1` | Number of replicas for the querier |
| querier.resources | object | `{}` | Resource requests and limits for the querier |
| querier.terminationGracePeriodSeconds | int | `30` | Grace period to allow the querier to shutdown before it is killed |
| querier.tolerations | list | `[]` | Tolerations for querier pods |
| queryFrontend.affinity | string | Hard node and soft zone anti-affinity | Affinity for query-frontend pods. Passed through `tpl` and, thus, to be configured as string |
| queryFrontend.extraArgs | list | `[]` | Additional CLI args for the query-frontend |
| queryFrontend.extraEnv | list | `[]` | Environment variables to add to the query-frontend pods |
| queryFrontend.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the query-frontend pods |
| queryFrontend.image.registry | string | `nil` | The Docker registry for the query-frontend image. Overrides `loki.image.registry` |
| queryFrontend.image.repository | string | `nil` | Docker image repository for the query-frontend image. Overrides `loki.image.repository` |
| queryFrontend.image.tag | string | `nil` | Docker image tag for the query-frontend image. Overrides `loki.image.tag` |
| queryFrontend.nodeSelector | object | `{}` | Node selector for query-frontend pods |
| queryFrontend.podAnnotations | object | `{}` | Annotations for query-frontend pods |
| queryFrontend.replicas | int | `1` | Number of replicas for the query-frontend |
| queryFrontend.resources | object | `{}` | Resource requests and limits for the query-frontend |
| queryFrontend.terminationGracePeriodSeconds | int | `30` | Grace period to allow the query-frontend to shutdown before it is killed |
| queryFrontend.tolerations | list | `[]` | Tolerations for query-frontend pods |
| serviceAccount.annotations | object | `{}` | Annotations for the service account |
| serviceAccount.create | bool | `true` | Specifies whether a ServiceAccount should be created |
| serviceAccount.imagePullSecrets | list | `[]` | Image pull secrets for the service account |
| serviceAccount.name | string | `nil` | The name of the ServiceAccount to use. If not set and create is true, a name is generated using the fullname template |
| serviceMonitor.annotations | object | `{}` | ServiceMonitor annotations |
| serviceMonitor.enabled | bool | `false` | If enabled, ServiceMonitor resources for Prometheus Operator are created |
| serviceMonitor.interval | string | `nil` | ServiceMonitor scrape interval |
| serviceMonitor.labels | object | `{}` | Additional ServiceMonitor labels |
| serviceMonitor.namespace | string | `nil` | Alternative namespace for ServiceMonitor resources |
| serviceMonitor.namespaceSelector | object | `{}` | Namespace selector for ServiceMonitor resources |
| serviceMonitor.scrapeTimeout | string | `nil` | ServiceMonitor scrape timeout in Go duration format (e.g. 15s) |
| tableManager.affinity | string | Hard node and soft zone anti-affinity | Affinity for table-manager pods. Passed through `tpl` and, thus, to be configured as string |
| tableManager.enabled | bool | `false` | Specifies whether the table-manager should be enabled |
| tableManager.extraArgs | list | `[]` | Additional CLI args for the table-manager |
| tableManager.extraEnv | list | `[]` | Environment variables to add to the table-manager pods |
| tableManager.extraEnvFrom | list | `[]` | Environment variables from secrets or configmaps to add to the table-manager pods |
| tableManager.image.registry | string | `nil` | The Docker registry for the table-manager image. Overrides `loki.image.registry` |
| tableManager.image.repository | string | `nil` | Docker image repository for the table-manager image. Overrides `loki.image.repository` |
| tableManager.image.tag | string | `nil` | Docker image tag for the table-manager image. Overrides `loki.image.tag` |
| tableManager.nodeSelector | object | `{}` | Node selector for table-manager pods |
| tableManager.podAnnotations | object | `{}` | Annotations for table-manager pods |
| tableManager.replicas | int | `1` | Number of replicas for the table-manager |
| tableManager.resources | object | `{}` | Resource requests and limits for the table-manager |
| tableManager.terminationGracePeriodSeconds | int | `30` | Grace period to allow the table-manager to shutdown before it is killed |
| tableManager.tolerations | list | `[]` | Tolerations for table-manager pods |

## Configuration

This chart configures Loki in microservices mode.
The chart can be installed with defaults out of the box.
As such, it runs two replicas of ingester and one replica for each of the other components using BoltDB as storage.
Ingester is run as a StatefulSet so each Pod gets its own persistent volume.

The chart does not support setting up Consul or Etcd for discovery.
These would have to be set up separately.
Instead, memberlist can be used which does not require a separate key/value store.
The chart creates a headless service for the memberlist which ingester, distributor, and querier are part of.

### Example configuration using memberlist, boltdb-shipper, and S3 for storage

Note that `loki.config` must be configured as string.
That's required because it is passed through the `tpl` function in order to support templating.
This means that a complete configuration needs to be supplied to the charts which is a good thing anyways.
Also, this allows using a separate YAML file which can be passed using `--set-file loki.config=<path to config file>`.

```yaml
loki:
  config: |
    server:
      log_level: info
      # Must be set to 3100
      http_listen_port: 3100

    distributor:
      ring:
        kvstore:
          store: memberlist

    ingester:
      # Disable chunk transfer which is not possible with statefulsets
      # and unnecessary for boltdb-shipper
      max_transfer_retries: 0
      chunk_idle_period: 1h
      chunk_target_size: 1536000
      max_chunk_age: 1h
      lifecycler:
        join_after: 0s
        ring:
          kvstore:
            store: memberlist

    memberlist:
      join_members:
        - {{ include "loki.fullname" . }}-memberlist

    limits_config:
      ingestion_rate_mb: 10
      ingestion_burst_size_mb: 20
      max_concurrent_tail_requests: 20
      max_cache_freshness_per_query: 10m

    schema_config:
      configs:
        - from: 2020-09-07
          store: boltdb-shipper
          object_store: aws
          schema: v11
          index:
            prefix: loki_index_
            period: 24h

    storage_config:
      aws:
        s3: s3://eu-central-1
        bucketnames: my-loki-s3-bucket
      boltdb_shipper:
        active_index_directory: /var/loki/index
        shared_store: s3
        cache_location: /var/loki/cache

    query_range:
      # make queries more cache-able by aligning them with their step intervals
      align_queries_with_step: true
      max_retries: 5
      # parallelize queries in 15min intervals
      split_queries_by_interval: 15m
      cache_results: true

      results_cache:
        cache:
          enable_fifocache: true
          fifocache:
            max_size_items: 1024
            validity: 24h

    frontend_worker:
      frontend_address: {{ include "loki.queryFrontendFullname" . }}:9095

    frontend:
      log_queries_longer_than: 5s
      compress_responses: true
```
