# radarr movie download client

This is a helm chart for [radarr](https://github.com/Radarr/Radarr/) leveraging the [Linuxserver.io image](https://hub.docker.com/r/linuxserver/radarr/)

## TL;DR;

```shell
$ helm repo add billimek https://billimek.com/billimek-charts/
$ helm install billimek/radarr
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release billimek/radarr
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
helm delete my-release --purge
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Sentry chart and their default values.

| Parameter                  | Description                         | Default                                                 |
|----------------------------|-------------------------------------|---------------------------------------------------------|
| `image.repository`         | Image repository | `linuxserver/radarr` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/linuxserver/radarr/tags/).| `amd64-v0.2.0.1344-ls17`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `strategyType`             | Specifies the strategy used to replace old Pods by new ones | `Recreate` |
| `timezone`                 | Timezone the radarr instance should run as, e.g. 'America/New_York' | `UTC` |
| `puid`                     | process userID the radarr instance should run as | `1001` |
| `pgid`                     | process groupID the radarr instance should run as | `1001` |
| `Service.type`          | Kubernetes service type for the radarr GUI | `ClusterIP` |
| `Service.port`          | Kubernetes port where the radarr GUI is exposed| `7878` |
| `Service.annotations`   | Service annotations for the radarr GUI | `{}` |
| `Service.labels`        | Custom labels | `{}` |
| `Service.loadBalancerIP` | Loadbalance IP for the radarr GUI | `{}` |
| `Service.loadBalancerSourceRanges` | List of IP CIDRs allowed access to load balancer (if supported)      | None
| `ingress.enabled`              | Enables Ingress | `false` |
| `ingress.annotations`          | Ingress annotations | `{}` |
| `ingress.labels`               | Custom labels                       | `{}`
| `ingress.path`                 | Ingress path | `/` |
| `ingress.hosts`                | Ingress accepted hostnames | `chart-example.local` |
| `ingress.tls`                  | Ingress TLS configuration | `[]` |
| `persistence.config.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.config.size`         | Size of persistent volume claim | `1Gi` |
| `persistence.config.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.config.storageClass` | Type of persistent volume claim | `-` |
| `persistence.config.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.downloads.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.downloads.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.downloads.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.downloads.storageClass` | Type of persistent volume claim | `-` |
| `persistence.downloads.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.movies.enabled`      | Use persistent volume to store configuration data | `true` |
| `persistence.movies.size`         | Size of persistent volume claim | `10Gi` |
| `persistence.movies.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.movies.storageClass` | Type of persistent volume claim | `-` |
| `persistence.movies.accessMode`  | Persistence access mode | `ReadWriteOnce` |
| `persistence.extraExistingClaimMounts`  | Optionally add multiple existing claims | `[]` |
| `resources`                | CPU/Memory resource requests/limits | `{}` |
| `nodeSelector`             | Node labels for pod assignment | `{}` |
| `tolerations`              | Toleration labels for pod assignment | `[]` |
| `affinity`                 | Affinity settings for pod assignment | `{}` |
| `podAnnotations`           | Key-value pairs to add as pod annotations  | `{}` |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
helm install --name my-release \
  --set timezone="America/New York" \
    billimek/radarr
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install --name my-release -f values.yaml stable/radarr
```

Read through the [values.yaml](https://github.com/billimek/billimek-charts/blob/master/radarr/values.yaml) file. It has several commented out suggested values.