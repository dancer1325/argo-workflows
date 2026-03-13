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

* You can use Kustomize to patch your preferred [configurations](managed-namespace.md)

#### Full CRDs

* requirements
  * Argo Workflow v4.0+,    
    * [FULL CRDs](../manifests/base/crds/full)
  * Argo Workflow v4.0-,
    * [minimal CRDs](../manifests/base/crds/minimal)

#### -- via -- Helm Chart

* [Helm charts](https://github.com/argoproj/argo-helm)

## Installation options

Determine your base installation option.

* A **cluster install** will watch and execute workflows in all namespaces
* This is the default installation option when installing using the official release manifests.
* A **namespace install** only executes workflows in the namespace it is installed in (typically `argo`)
* Look for `namespace-install.yaml` in the [release assets](https://github.com/argoproj/argo-workflows/releases/latest).
* A **managed namespace install**: only executes workflows in a separate namespace from the one it is installed in
* See [Managed Namespace](managed-namespace.md) for more details.

## Additional installation considerations

Review the following:

* [Workflow RBAC](workflow-rbac.md)
* [Security](security.md).
* [Scaling](scaling.md) and [running at massive scale](running-at-massive-scale.md).
* [High-availability](high-availability.md)
* [Disaster recovery](disaster-recovery.md)
