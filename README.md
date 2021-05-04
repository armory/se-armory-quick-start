# se-armory-quick-start

## This is a wip to streamline the armory spinnaker quick start process. Goals of this work are:
* Minimize amount of steps required to bootstrap a minimum spinnaker service that can deploy a manifest to spinnaker cluster namespace (Ideally, fewer than 5 commands)
* Provide a quick start for those that have a k8s cluster that meetss pre-reqs and those that have no cluster
* Provide description of kustomize repo and purpose
* Provide description of minnaker and purpose

------------------
# Armory Spinnaker Quick Start

## Overview

This Spinnaker quick start creates a minimaly functional instance. You will be able to deploy K8s manifests to your Spinnaker install cluster. It provides no security configuration and leverages an insecure object store. It is intended to prvoide you with a quick and easy method to tour the Spinnaker management console, and the ability to configure a basic pipeline manifest deploy stage.

For more in-depth configuration, we recoomend cloning the Armroy kustomize patch repo for Spinnaker. If you do not have a K8s cluster that meets the minimum prerequisites, you can use the quick start scripts for Minnaker with a linux host you provision. Minnaker is the easiest method for deploying Armory Spinnaker as it includes a number of helper scripts.

### Prerequisites

A K8s cluster with:
* LoadBalancer service
* Default storage class
* If you don't have a K8s cluster, you can use the Armory [Minnaker](https://github.com/armory/minnaker) K3s install option

## Install Armory Operator, deploy Spinnaker, deploy a pod from a pipeline.

### Deploy Armory Operator

<code>kubectl apply -f https://github.com/natereid72/armory-operator/raw/main/armory-operator.yaml</code>

### Deploy Minimal Spinnaker

To deploy Spinnaker, clone the Armory Kustommize repo

<code>kubectl apply -k https://github.com/natereid72/armory-operator</code>

After deploying the spinnaker manifest, use <code>watch kubectl get spinsvc spinnaker -n spinnaker</code> to monitor the status. Once you see the url populated, use your web browser to access the Spinnaker UI. From there, you will be able to create an application, a pipeline, and a deploy manifest stage for the cluster you've installed Spinnaker on.
