# reports-server

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.0.1](https://img.shields.io/badge/AppVersion-v0.0.1-informational?style=flat-square)

TODO

## Installing the Chart

Add `reports-server` Helm repository:

```shell
helm repo add reports-server https://kyverno.github.io/reports-server/
```

Install `reports-server` Helm chart:

```shell
helm install reports-server --namespace reports-server --create-namespace reports-server/reports-server
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| postgresql.enabled | bool | `true` | Deploy postgresql dependency chart |
| postgresql.auth.postgresPassword | string | `"reports"` |  |
| postgresql.auth.database | string | `"reportsdb"` |  |
| apiServices.enabled | bool | `true` | Store reports in reports-server |
| apiServices.installEphemeralReportsService | bool | `true` | Store ephemeral reports in reports-server |
| nameOverride | string | `""` | Name override |
| fullnameOverride | string | `""` | Full name override |
| replicaCount | int | `1` | Number of pod replicas |
| image.registry | string | `"ghcr.io"` | Image registry |
| image.repository | string | `"kyverno/reports-server"` | Image repository |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy |
| image.tag | string | `nil` | Image tag (will default to app version if not set) |
| imagePullSecrets | list | `[]` | Image pull secrets |
| priorityClassName | string | `"system-cluster-critical"` | Priority class name |
| serviceAccount.create | bool | `true` | Create service account |
| serviceAccount.annotations | object | `{}` | Service account annotations |
| serviceAccount.name | string | `""` | Service account name (required if `serviceAccount.create` is `false`) |
| podAnnotations | object | `{}` | Pod annotations |
| podSecurityContext | object | `{"fsGroup":2000}` | Pod security context |
| securityContext | object | See [values.yaml](values.yaml) | Container security context |
| livenessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/livez","port":"https","scheme":"HTTPS"},"periodSeconds":10}` | Liveness probe |
| readinessProbe | object | `{"failureThreshold":3,"httpGet":{"path":"/readyz","port":"https","scheme":"HTTPS"},"initialDelaySeconds":20,"periodSeconds":10}` | Readiness probe |
| resources.limits | string | `nil` | Container resource limits |
| resources.requests | string | `nil` | Container resource requests |
| autoscaling.enabled | bool | `false` | Enable autoscaling |
| autoscaling.minReplicas | int | `1` | Min number of replicas |
| autoscaling.maxReplicas | int | `100` | Max number of replicas |
| autoscaling.targetCPUUtilizationPercentage | int | `80` | Target CPU utilisation |
| autoscaling.targetMemoryUtilizationPercentage | string | `nil` | Target Memory utilisation |
| nodeSelector | object | `{}` | Node selector |
| tolerations | list | `[]` | Tolerations |
| affinity | object | `{}` | Affinity |
| service.type | string | `"ClusterIP"` | Service type |
| service.port | int | `443` | Service port |
| config.debug | bool | `false` | Enable debug (to use inmemorydatabase) |
| config.db.host | string | `""` | Database host |
| config.db.name | string | `"reportsdb"` | Database name |
| config.db.user | string | `"postgres"` | Database user |
| config.db.password | string | `"reports"` | Database password |

## Source Code

* <https://github.com/kyverno/reports-server>

## Requirements

Kubernetes: `>=1.16.0-0`

| Repository | Name | Version |
|------------|------|---------|
| oci://registry-1.docker.io/bitnamicharts | postgresql | 13.4.1 |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Nirmata | <cncf-kyverno-maintainers@lists.cncf.io> | <https://kyverno.io/> |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
