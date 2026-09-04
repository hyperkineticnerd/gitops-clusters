= Red Hat Advanced Cluster Management (RHACM)

== What is it?

Red Hat's offical page for RHACM describes it as, "end-to-end management, visibility, and control of your entire fleet from a single console, with operational policies built in." and expands RHACM benefits for Red Hat OpenShift, "deploying apps, managing multiple clusters, and enforcing policies across multiple clusters deployed to datacenter, cloud, and edge environments".

== Why are we using it?

We use RHACM for its deployment capabilities and its integration with OpenShift GitOps. We rely on GitOps for the deploying apps and enforcing policies, and leave RHACM for deploying clusters. We have greater granularity of enforcement of policies using GitOps, we can automatically enforce the configuration and installation of operational components on the cluster, or we can use GitOps to carefully, cautiously, and meticulously control the installation and configuration of components. GitOps also provides us with an external audit trail of changes for clusters through Git commits and merge requests.

== Where do we start?

=== GitOpsCluster

The GitOpsCluster CR creates the link between RHACM and ArgoCD, it tells RHACM to create cluster `Secrets` for ArgoCD.

Example:
[source,yaml]
-----
apiVersion: apps.open-cluster-management.io/v1beta1
kind: GitOpsCluster
metadata:
  name: gitops-clusters
  namespace: openshift-gitops
spec:
  argoServer:
    argoNamespace: openshift-gitops
    cluster: local-cluster
  createBlankClusterSecrets: false
  createPolicyTemplate: true
  gitopsAddon:
    argoCDAgent:
      enabled: false
      propagateHubCA: true
    enabled: false
    overrideExistingConfigs: true
  placementRef:
    apiVersion: cluster.open-cluster-management.io/v1beta1
    kind: Placement
    name: all-openshift-clusters-except-local
    namespace: openshift-gitops
-----

=== ManagedClusterSetBinding

The ManagedClusterSetBinding ...
