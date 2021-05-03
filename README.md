# se-armory-quick-start

## This is a wip to streamline the armory spinnaker quick start process. Goals of this work are:
* Minimize amount of steps required to bootstrap a minimum spinnaker service that can deploy a manifest to spinnaker cluster namespace (Ideally, fewer than 5 commands)
* Provide a quick start for those that have a k8s cluster that meetss pre-reqs and those that have no cluster
* Provide description of kustomize repo and purpose
* Provide description of minnaker and purpose

------------------
# Armory Spinnaker Quick Start

## Prerequisites

A K8s cluster with:
* LoadBalancer service
* Default storage class
* If you don't have a K8s cluster, you can use the Armory [Minnaker](https://github.com/armory/minnaker) K3s install 

## Install Armory Operator, deploy Spinnaker, deploy a pod from a pipeline.

### Deploy Armory Operator

<code>kubectl apply -f https://github.com/natereid72/armory-operator/raw/main/armory-operator.yaml</code>

### Deploy Minimal Spinnaker

To deploy Spinnaker, clone the Armory Kustommize repo

<code>git clone https://github.com/armory/spinnaker-kustomize-patches.git</code>
