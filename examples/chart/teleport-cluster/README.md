# Teleport Cluster

This chart sets up a single node Teleport cluster.
It uses a persistent volume claim for storage.
Great for getting started with Teleport.

It can also deploy HA Teleport clusters on EKS, GKE, and other Kubernetes clusters.
See our [Helm guides](https://goteleport.com/docs/kubernetes-access/helm/guides) for details.

## Getting Started

Install Teleport in a separate namespace and provision a web certificate using
Let's Encrypt:

```bash
$ helm install teleport/teleport-cluster \
    --set acme=true \
    --set acmeEmail=alice@example.com \
    --set clusterName=teleport.example.com\
    --create-namespace \
    --namespace=teleport-cluster \
    ./teleport-cluster/
```

## Uninstalling

```bash
helm uninstall teleport-cluster
```

## Arguments Reference

To use The enterprise version, set `--set=enterprise=true` value and create a
secret `license` in the chart namespace.

Check [our documentation](https://goteleport.com/teleport/docs) for more details.

| Name                      | Description                                                                 | Default                                                | Required |
|---------------------------|-----------------------------------------------------------------------------|--------------------------------------------------------|----------|
| `clusterName`             | Teleport cluster name (must be an FQDN)                                     |                                                        | yes      |
| `teleportVersionOverride` | Teleport version                                                            | Current stable version                                 | no       |
| `image`                   | OSS Docker image                                                            | `quay.io/gravitational/teleport`                       | no       |
| `enterpriseImage`         | Enterprise Docker image                                                     | `quay.io/gravitational/teleport-ent`                   | no       |
| `acme`             | Enable ACME support in Teleport (Letsencrypt.org)                           | `false`                                                | no       |
| `acmeEmail`               | Email to use for ACME certificates                                          |                                                        | no       |
| `acmeURI`                 | ACME server to use for certificates                                         | `https://acme-v02.api.letsencrypt.org/directory`       | no       |
| `labels.[name]`           | Key-value pairs, for example `--labels.env=local --labels.region=us-west-1` |                                                        | no       |
| `enterprise`              | Use Teleport Enterprise                                                     | `false`                                                | no       |

## Guides

See our [Helm guides](https://goteleport.com/docs/kubernetes-access/helm/guides) for information on setting up
high availability Teleport clusters in EKS or GKE, plus a more comprehensive chart reference.
