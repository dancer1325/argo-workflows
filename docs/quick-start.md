# Quick Start

* goal
  * try out Argo Workflows

* approaches
  * locally
  * [Killercoda course](training.md#hands-on)
    * pros: skip set up a Kubernetes cluster 

## Prerequisites

* running Kubernetes cluster    
  * locally
    * ways
      * [minikube](https://minikube.sigs.k8s.io/docs/)
      * [kind](https://kind.sigs.k8s.io/)
      * [k3s](https://k3s.io/) or [k3d](https://k3d.io/)
      * [Docker Desktop](https://www.docker.com/products/docker-desktop/)
  * | [production](installation.md)
* `kubectl`

## steps
### Install Argo Workflows

```bash
kubectl create namespace argo
kubectl apply --server-side -n argo -f /manifests/quick-start-minimal.yaml
```

### Install the Argo Workflows CLI

* [here](walk-through/argo-cli.md)

### Submit an example workflow

* ways
  * [-- via -- CLI](#---via----cli)
  * [-- via -- UI](#---via----ui)

#### -- via -- CLI

```bash
# --watch
#   responsible for
#     watches the workflow / it runs
#     reports whether it succeeds OR not
#   ONCE workflow completes -> the watch stops
argo submit -n argo --watch /examples/hello-world.yaml

# check submitted Workflows
#   hello-world-<SOME_RANDOM_CHARACTERS>
#     Reason of <SOME_RANDOM_CHARACTERS>:🧠give Workflows UNIQUE names🧠
#       DIFFERENT <SOME_RANDOM_CHARACTERS> / EACH `argo submit` command  
argo list -n argo

# OR
#   @latest
#     == the latest Workflow run
argo get -n argo @latest

# check submitted Workflows run
argo logs -n argo @latest
```

#### -- via -- UI

* steps
  * `kubectl -n argo port-forward service/argo-server 2746:2746`
    * if you [install Argo Workflow via Helm chart](https://github.com/argoproj/argo-helm/tree/main/charts/argo-workflows) -> `kubectl -n argo port-forward service/argo-workflows-server 2746:2746`
  * | browser,
    * https://localhost:2746
      * \> Submit New Workflow > Edit using full workflow options > Create
