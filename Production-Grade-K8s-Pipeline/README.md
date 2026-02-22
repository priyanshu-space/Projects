# Production-Grade Jenkins Pipeline for GKE

Enterprise-ready CI/CD pipeline for deploying hardened applications to Google Kubernetes Engine.

## Features

- **Infrastructure:** Private GKE cluster, custom VPC, Cloud NAT.
- **Security Gates:** Checkov (IaC), Gitleaks (Secrets), OWASP Dependency-Check, Trivy (Image), Kube-score (K8s), OWASP ZAP (DAST).
- **Hardening:** Kyverno admission control, non-root containers, resource limits.
- **Reliability:** Atomic Helm deployments, Prometheus SLO monitoring.

## Project Structure

```text
├── app/
├── helm/
├── terraform/
├── policies/
├── observability/
└── Jenkinsfile
```

## How to Deploy

1. **Infrastructure:**
   ```bash
   cd terraform
   terraform init
   terraform apply -var="project_id=YOUR_PROJECT"
   ```
2. **Setup Jenkins:**
   - Install the "Kubernetes" and "Slack" plugins.
   - Configure a Pipeline job pointing to this repository.
3. **Wait for Approval:** The pipeline will pause before the Production stage for manual review of security reports.
