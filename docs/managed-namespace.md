# Managed Namespace

* requirements
  * v2.5+

* ways to install Argo
  * extend Kubernetes API -- via -- Argo CRD
    * requirements
      * "admin" roles
        * Reason:🧠CRDs == cluster-scoped objects🧠
  * -- based on -- the scope
    * | namespace-scoped
      * -> install Roles
      * requirements
        * install Workflow Controller & Argo Server -- via -- `--namespaced`
      * if you want to run workflows | separate namespace -> add `--managed-namespace`
    * | cluster-scoped
      * -> install ClusterRoles
      * ❌NOT use❌
        * `--namespaced`
        * `--managed-namespace`


* TODO: 
!!! Info "Example Use Case"
    You can use a managed namespace install if you want some users or services to run Workflows without granting them privileges in the namespace where Argo Workflows is installed.
    For example, if you only run CI/CD Workflows that are maintained by the same team that manages the Argo Workflows installation, you may want a namespace install.
    But if all the Workflows are run by a separate data science team, you may want to give them a "data-science-workflows" namespace and use a managed namespace install of Argo Workflows in another namespace.
