# gitops-manifests

Desired state of the EKS cluster. ArgoCD watches this repo; a commit here is a deployment.

| Path | What |
|---|---|
| `apps/` | ArgoCD Applications (children of the root app-of-apps) |
| `charts/portfolio/` | Helm chart: Deployment (anti-affinity, probes, preStop), Service, Ingress (ALB), PDB |
| `envs/dev/values.yaml` | Dev image tag, **updated by Jenkins** automatically |
| `envs/prod/values.yaml` | Prod image tag, promoted by commit, synced manually in ArgoCD |
| `platform/ingressclass/` | ALB IngressClass for EKS Auto Mode |
| `platform/kyverno-policies/` | CEL ValidatingPolicies: ECR only, no latest, limits required |

Monitoring (kube-prometheus-stack, Loki, Alloy) and Kyverno are Helm charts referenced from `apps/`.
