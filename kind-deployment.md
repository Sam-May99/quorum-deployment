# Deploying the KinD cluster

[KinD](https://kind.sigs.k8s.io/docs/user/quick-start/) is a runtime allowing for k8s clusters to be configured on local machines in a similar way to [MiniKube](https://minikube.sigs.k8s.io/docs/start/). KinD has been used with this project to deploy the resources, and you should be able to use the same scripts to replicate my results. This document assumes you're using a Mac.

## Installing KinD

KinD can be installed through brew `brew install kind`

## Initialise the Cluster

Once KinD is installed, clone this repo and from the root of the project run the command `kind create cluster --config kind-config.yaml`. This will configure the KinD cluster to start and attach the volumes for the Quorum nodes on the cluster to be able to access.*1

## Deleting the Cluster

`kind delete cluster`*2

## Gotcha's

1. The contents of the configuration file will need to be altered to match the `examples/` directory from your local copy of the [quorum-tools](https://github.com/kaleido-io/quorum-tools) repository. If this is not done correctly, when you start the quorum nodes they will be unable to correctly get the chain information and initialise.
2. When bringing up/down the cluster frequently, it's possible for the Docker runtime to get into a bit of a funky state, in this case restarting the docker process should be sufficient the fix the problem, on one case I did need to restart the entire machine.
3. Through the docker engine interface it's recommended when using the quorum examples to expend the allowed memory for the containers up to 8Gi as the nodes and the racecourse applications can consume a lot of memory and instability is not always easy to spot.