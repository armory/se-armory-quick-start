# se-armory-quick-start

## This is a wip to streamline the armory spinnaker quick start process. Goals of this work are:
* Minimize amount of steps required to bootstrap a minimum spinnaker service that can deploy a manifest to spinnaker cluster namespace (Ideally, fewer than 5 commands)
* Provide a quick start for those that have a k8s cluster that meets pre-reqs and those that have no cluster
* Provide description of kustomize repo and purpose
* Provide description of minnaker and purpose

------------------
# Armory Spinnaker Quick Start

### Overview

This Spinnaker quick start creates a minimaly functional instance and deploys Spinnaker with Armory components (This deployment of Armory Spinnaker requires an entitlement license from Armory for commercial use). You will be able to deploy K8s manifests to your Spinnaker install cluster. It provides no security configuration and leverages an insecure object store. It is intended to prvoide you with a quick and easy method to tour the Spinnaker management console, and the ability to configure a basic pipeline manifest deploy stage.

For more in-depth configuration, we recoomend cloning the [Armroy kustomize patch repo](https://github.com/armory/spinnaker-kustomize-patches) for Spinnaker. If you do not have a K8s cluster that meets the minimum prerequisites, you can use the quick start scripts for [Minnaker](https://github.com/armory/minnaker) with a linux host you provision. Minnaker is the easiest method for deploying thorughly functional Armory Spinnaker as it includes a number of helper scripts.

### Prerequisites

A K8s cluster with:
* LoadBalancer service
* Default storage class

## Install Armory Operator and deploy Armory Spinnaker

### Install Armory Operator and CRDs

<code>kubectl apply -k https://github.com/armory/se-armory-quick-start/operator</code>

### Deploy Minimal Spinnaker

<code>kubectl apply -k https://github.com/armory/se-armory-quick-start/spinnaker</code>

After deploying the spinnaker manifest, use <code>watch kubectl get spinsvc spinnaker -n spinnaker</code> to monitor the status. Once you see the url populated, use your web browser to access the Spinnaker UI. From there, you will be able to create an application, a pipeline, and a deploy manifest stage for the cluster you've installed Spinnaker on.
