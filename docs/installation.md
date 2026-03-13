# Installation

## Non-production installation

* goal
  * install Argo Workflows | non-production environment OR desktop (minikube/kind/k3d etc)
* [here](quick-start.md)

## Production installation

### Installation Methods

#### Official release manifests

* [releases page](https://github.com/argoproj/argo-workflows/releases/latest) | "Controller and Server" section
  * run `kubectl` commands

    ```yaml
    kubectl create namespace argo
    
    # Install the manifest
    kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/vSOMEVERSION/install.yaml
    # _Example:_ v4.0.2
    kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v4.0.2/install.yaml
    ```

* if you want to personalize the Argo installation -> use Kustomize
  * _Examples:_ [here](../manifests)

#### Full CRDs

* requirements
  * Argo Workflow v4.0+,    
    * [FULL CRDs](../manifests/base/crds/full)
  * Argo Workflow v4.0-,
    * [minimal CRDs](../manifests/base/crds/minimal)

#### -- via -- Helm Chart

* [Helm charts](https://github.com/argoproj/argo-helm)

## Installation options

* **cluster install**
  * watch & execute workflows | ALL namespaces
  * | [install official releases](#official-release-manifests),
    * default one
  * [manifests](../manifests/cluster-install)
* **namespace install**
  * ONLY executes workflows | namespace / workflow is installed
    * by default, "argo"
  * [manifest](../manifests/namespace-install)
* **managed namespace install**
  * ONLY executes workflows | namespace / != | namespace is installed in
  * [how to install](managed-namespace.md)

## Additional installation considerations

Review the following:

* [Workflow RBAC](workflow-rbac.md)
* [Security](security.md).
* [Scaling](scaling.md) and [running at massive scale](running-at-massive-scale.md).
* [High-availability](high-availability.md)
* [Disaster recovery](disaster-recovery.md)
