# helm-charts for UPM

helm charts to install upm



To install the `gateway`、`user`:

```bash
$ helm repo add upm-charts https://upmio.github.io/helm-charts
$ helm install gateway upm-charts/upm-gateway-ms
$ helm install user upm-charts/upm-user-ms
```



To uninstall/delete the `my-release`:

```bash
$ helm uninstall my-release
```



To add new `charts`:

```bash
$ mkdir helm-charts/${new_charts_name}
$ mv ${new_chart_tgz_package} helm-charts/${new_charts_name} 
$ helm repo index helm-charts --url https://upmio.github.io
```



## Parameters

### Global parameters

| Name                          | Description                         | Value |
| ----------------------------- | ----------------------------------- | ----- |
| `global.auth.username`        | Name for a custom user to create    | `""`  |
| `global.auth.password`        | Password for the new user           | `""`  |
| `global.auth.monitorUsername` | Name for ProxySQL user to create    | `""`  |
| `global.auth.monitorPassword` | Password for ProxySQL ser to create | `""`  |

### Common parameters

| Name           | Description                                              | Value               |
| -------------- | -------------------------------------------------------- | ------------------- |
| `architecture` | MySQL architecture (`standalone` or `group-replication`) | `group-replication` |

### Gateway common parameters

| Name                       | Description                                                  | Value             |
| -------------------------- | ------------------------------------------------------------ | ----------------- |
| `image.registry`           | MySQL image registry                                         | `docker.io`       |
| `image.repository`         | MySQL image repository                                       | `haolowkey/mysql` |
| `image.tag`                | MySQL image tag (immutable tags are recommended)             | `8.0.26`          |
| `image.pullPolicy`         | MySQL image pull policy                                      | `IfNotPresent`    |
| `image.pullSecrets`        | Specify docker-registry secret names as an array             | `[]`              |
| `auth.replicationUser`     | MySQL replication user                                       | `replicator`      |
| `auth.replicationPassword` | MySQL replication user password. Ignored if existing secret is provided | `""`              |
