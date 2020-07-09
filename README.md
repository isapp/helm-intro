# Wrangling Your Deployments With CI/CD & Helm

## First Thank you
1. Connecting is hard this meetup is awesome
1. Hosting and organizing


## Who am I?

* I'm Austin Vance. I have done a few things mostly coding or
managing operations teams. 

* I have a history at Pivotal, EMC, Dell, 
and Paypal.

* Now I have Focused Labs and we are a growing amazing team!
  * Focused's goal is to bring agility to operations and software development

## Why Kubernetes

1. Config driven deployments
1. Containers are first class
1. Multi cloud by design
1. No Magic
1. Really fun to operate
1. Really fun to deploy to

### BUT - Kubernetes is hard - it's a lot to learn

* A single app nees Pod, deployment, replicaset, service, ingress, networkpolicy, and a lot more
* Updates, rollbacks, and roll outs require some forethought
* Unique deployments for different environemnts are impossible with native objects (if we ignore kustomize... that's for a different talk)

## In comes Helm

What is helm?

> Helm is a templeting engine and deployment manager for kubernetes.

But it's become so much more... 

Helm is an:
- ecosystem of software you can run on kubernetes with standard reasonable config
- a dependncy managment system
- a rollback rollforward manager
- a configuration a code manager

# Lets deploy something with helm

![helm deploy](https://github.com/focused-labs/helm-intro/blob/master/helm-install.gif?raw=true)
