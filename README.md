# Quorum-Deployment

Scripts and tools required for deployment of the [Quorum application](https://github.com/kaleido-io/quorum).

The manifests and charts in this repository are intended for use with a KIND cluster, which will need to be started using the configuration file provided, and will require volumes to be mpounted in the correct locations.

## Development Files

Under the `manual/` directory are the manifests used during the development of this project, all are in a rough-and-ready state and are not intended or validated for production usage.

## Quorum Helm Chart

Under the `quorum-deployment` directory is the helm chart for deploying 4 Quorum nodes, and a bootnode to a Kubernetes cluster with associated persistence for the chain data. This helm chart is under active development.

,mken