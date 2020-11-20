# Wrangling Your Deployments With CI/CD & Helm

---

## Why Kubernetes

1. Config driven deployments
1. Containers are first class
1. Multi cloud by design
1. No Magic
1. Really fun to operate
1. Really fun to deploy to

---

### BUT - Kubernetes is hard - it's a lot to learn

* A single app nees Pod, deployment, replicaset, service, ingress, networkpolicy, and a lot more
* Updates, rollbacks, and roll outs require some forethought
* Unique deployments for different environemnts are impossible with native objects (if we ignore kustomize... that's for a different talk)

---

## In comes Helm

What is helm?

> Helm is a templeting engine and deployment manager for kubernetes.

But it's become so much more... 

Helm is an:
- ecosystem of software you can run on kubernetes with standard reasonable config
- a dependncy managment system
- a rollback rollforward manager
- a configuration a code manager

### Why Helm

* Helm is easy!
* Written in GoLang
* The templates look intimidating at first but there's not much to it
* Helps organize all your k8s configuration
* Easily parameterize dynamic k8s config between environments
* Install, upgrade, rollback for a package of k8s config files
* Version tracking

### Lets deploy something with helm

![helm deploy](https://github.com/focused-labs/helm-intro/blob/master/helm-install.gif?raw=true)


### How about an upgrade

![helm upgrade](https://github.com/focused-labs/helm-intro/blob/master/helm-upgrade.gif?raw=true)

### Creating your own
`helm create <name>`

Let's take a look at what gets created.

### Golang Templating Language
* Helm uses the Go templating language with [Sprig functions included](http://masterminds.github.io/sprig/)
* --dry-run will help you verify templated yaml
* [My source of friendly reminder YAML docs](https://learnxinyminutes.com/docs/yaml/)
* Looks intimidating at first, but it's really not all that and a bag of chips

Pro Tips:
1. SHA sum config/secrets to force pod restarts in deployment.yaml

# Now lets talk some CI

> ** Github actions on every project **

**Application version:** `<env>_<git_sha>`

**Audit Artifacts:**
1. Application Artifact: Docker image containing your built application. Published to an [ECR](https://aws.amazon.com/ecr/) repository under `<aws_account_number>.dkr.ecr.<aws_region>.amazonaws.com/<ecr_repo_name>:<application_version>`
1. Automated Test Artifact: Publish test result <nexus/S3/etc>
1. Manual Test Artifact: Acceptance of pviotal stories indicate that a representative of the business has manually interacted with the feature and verified it works as expected.
1. Automated vulnerability scanning before promotion: 
    * passing builds are candidates for promotion to staging/production.

# FluxCD & GitOps

> GitOps is two things:
>
> An operating model for Kubernetes and cloud native.  It provides a set of best practices to join up deployment, management and monitoring for containerized clusters and applications.  An elegant “1 slide” definition from Luis Faceira is shown below.
>
> ![GitOps Slide](https://github.com/focused-labs/helm-intro/blob/master/vitorsilva-gitops.png?raw=true)
>
> A path towards a developer centric experience for managing applications.  We’re applying the Git workflow to operations, as well as development.  Note that this is not just about Git push, it’s about how we set up the entire CICD toolchain and UI/UX.

## For gitops we use FluxCD

![Flux](https://github.com/focused-labs/helm-intro/blob/master/flux-cd-diagram.png?raw=true)


### Further Reading
* [Helm Hub](https://hub.helm.sh/)
* [Concourse](https://concourse-ci.org/)
* [FluxCD](https://https://fluxcd.io/)

