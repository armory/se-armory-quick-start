# se-armory-quick-start

## This is a wip to streamline the armory spinnaker quick start process. Goals of this work are:
* Minimize amount of steps required to bootstrap a minimum spinnaker service that can deploy a manifest to spinnaker cluster namespace (Ideally, fewer than 5 commands)
* Provide a quick start for those that have a k8s cluster that meets pre-reqs and those that have no cluster
* Provide description of kustomize repo and purpose
* Provide description of minnaker and purpose

------------------
# Armory Spinnaker Quick Start

### Overview

There are a few options to quickly install Armory Spinnaker. This Spinnaker quick start creates a minimally functional instance of Spinnaker with Armory components (_This deployment of Armory Spinnaker requires an entitlement license from Armory for commercial use_). It provides no security configuration and leverages an insecure object store. It is intended to provide you with a quick and easy method to tour the Spinnaker management console and ability to configure a basic pipeline.

For more in-depth configuration, we recommend cloning the [Armroy kustomize patch repo](https://github.com/armory/spinnaker-kustomize-patches) for Spinnaker. The kustomize repo includes shell scripts to simplify the process of deploying and maintaing a fully configured Spinnaker service. 

If you do not have a Kubernetes cluster, you can use the [Minnaker](https://github.com/armory/minnaker) quick start. Minnaker installs a self-contained K3s Kubernetes cluster and Spinnaker on a single linux VM, and leverages the kustomize repo for configuration.

## Prerequisites

A Kubernetes cluster with:
* LoadBalancer service
* Default storage class

## Install Armory Operator and deploy Armory Spinnaker

#### Install Armory Operator and CRDs

```
kubectl apply -k https://github.com/armory/se-armory-quick-start/operator
```

Use watch to monitor the operator pod until 2/2 containers show ready before proceeding. Use ```CTRL``` + ```C``` to exit:

```
watch kubectl get po -n spinnaker-operator
```

#### Deploy Minimal Spinnaker

```
kubectl apply -k https://github.com/armory/se-armory-quick-start/spinnaker
```

After deploying the spinnaker manifest, use watch to monitor the status. Once the status shows ```OK``` (note: It may show a status of ```failure``` momentarily), use your web browser to access the Spinnaker UI at the address listed under ```URL```

```
watch kubectl get po -n spinnaker
```

## Cleanup/Remove

```
kubectl delete -k https://github.com/armory/se-armory-quick-start/operator
```

```
kubectl delete -k https://github.com/armory/se-armory-quick-start/spinnaker
```
