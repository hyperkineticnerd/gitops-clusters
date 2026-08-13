# Single Repo, Multiple Clusters GitOps Example

## Entrypoint

The main gitops entrypoint is `/bootstrap/gitops.yaml`. The bootstrap ApplicationSet polls the `applicationset/` directory in Git
for additional ApplicationSets to deploy. Most of the ApplicationSets targets a specific environment and clusters labeled with
those environments.

## References

* [Multicloud Integrations](https://github.com/stolostron/multicloud-integrations)
* [Red Hat COP - Helm Charts](https://github.com/redhat-cop/helm-charts)
* [Red Hat COP - ACM Policies](https://github.com/redhat-cop/acm-policies)
* [RHACM GitOps](https://github.com/josgonza-rh/rhacm-gitops)
* [RHACM Policy](https://guifreelife.com/blog/2024/03/11/Placing-Open-Cluster-Management-Policies-on-Kubernetes/)
* [RHACM and Compliance Operator](https://jaosorior.dev/2021/writing-rhacm-policies-to-leverage-the-compliance-operator/)
