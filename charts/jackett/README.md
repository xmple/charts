# jackett televsion show download client

This is a helm chart for [jackett](https://github.com/jackett/jackett/) leveraging the [Linuxserver.io image](https://hub.docker.com/r/linuxserver/jackett/)

## TL;DR;

```shell
$ helm repo add xmple https://xmple.github.io/charts/
$ helm install xmple/jackett
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm install --name my-release xmple/jackett
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
| `image.repository`         | Image repository | `linuxserver/jackett` |
| `image.tag`                | Image tag. Possible values listed [here](https://hub.docker.com/r/linuxserver/jackett/tags/).| `amd64-latest`|
| `image.pullPolicy`         | Image pull policy | `IfNotPresent` |
| `updateStrategyType`             | Specifies the strategy used to replace old Pods by new ones | `RollingUpdate` |
| `timezone`                 | Timezone the jackett instance should run as, e.g. 'America/New_York' | `UTC` |
| `puid`                     | process userID the jackett instance should run as | `1001` |
| `pgid`                     | process groupID the jackett instance should run as | `1001` |
| `Service.type`          | Kubernetes service type for the jackett GUI | `ClusterIP` |
| `Service.port`          | Kubernetes port where the jackett GUI is exposed| `9117` |
| `Service.annotations`   | Service annotations for the jackett GUI | `{}` |
| `Service.labels`        | Custom labels | `{}` |
| `Service.loadBalancerIP` | Loadbalance IP for the jackett GUI | `{}` |
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
| `persistence.downloads.enabled`      | Use persistent volume for downloads | `true` |
| `persistence.downloads.size`         | Size of persistent volume claim | `1Gi` |
| `persistence.downloads.existingClaim`| Use an existing PVC to persist data | `nil` |
| `persistence.downloads.storageClass` | Type of persistent volume claim | `-` |
| `persistence.downloads.accessMode`  | Persistence access mode | `ReadWriteOnce` |
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
    xmple/jackett
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
helm install --name my-release -f values.yaml stable/jackett
```

Read through the [values.yaml](https://github.com/xmple/charts/blob/master/jackett/values.yaml) file. It has several commented out suggested values.
