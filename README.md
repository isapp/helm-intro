# Wrangling Your Deployments With CI/CD & Helm

---

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
* Helm uses the Go templating language with [Spring functions included](http://masterminds.github.io/sprig/)
* --dry-run will help you verify templated yaml
* [My source of friendly reminder YAML docs](https://learnxinyminutes.com/docs/yaml/)
* Looks intimidating at first, but it's really not all that and a bag of chips

Pro Tips:
1. SHA sum config/secrets to force pod restarts in deployment.yaml

# Now lets talk some CI

https://ci.withfocus.com

**Application version:** `<build_number>_<git_short_sha>`

**Audit Artifacts:**
1. Application Artifact: Docker image containing your built application. Published to an [ECR](https://aws.amazon.com/ecr/) repository under `<aws_account_number>.dkr.ecr.<aws_region>.amazonaws.com/<ecr_repo_name>:<application_version>`
1. Automated Test Artifact: Publish test result <nexus/S3/etc>
1. Manual Test Artifact: Acceptance of JIRA tickets indicate that a representative of the business has manually interacted with the feature and verified it works as expected.
1. Vulnerability Scanning: [WhiteHat Security](https://www.whitehatsec.com/) for vulnerability scanning.
    * Make sure you have a scanning schedule setup
    * Staging builds are candidates for promotion to production.
    * Confirming a valid security scan is a manual process.

### Further Reading
* [Helm Hub](https://hub.helm.sh/)
* [Vault Tutorial](https://www.vaultproject.io/docs/platform/k8s/helm/run)

