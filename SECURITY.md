# Security Policy — python-fawkes-path-gitops

## Supported versions

| Version       | Supported                                       |
| ------------- | ----------------------------------------------- |
| `main` branch | ✅ Active — patches applied here first          |
| Older commits | ❌ Git history only; ArgoCD always syncs `main` |

---

## Reporting a vulnerability

**Do not open a public GitHub issue for security vulnerabilities.**

Report privately using one of these channels, in order of preference:

1. **GitHub private vulnerability reporting** (preferred):
   [Security → Report a vulnerability](https://github.com/paruff/python-fawkes-path-gitops/security/advisories/new)
   — this keeps the report confidential until a fix is published.

2. **Email**: Contact the maintainer via the email address on the
   [paruff GitHub profile](https://github.com/paruff). Use the subject line
   `[python-fawkes-path-gitops] Security report`.

Include in your report:

- Affected manifest, image reference, RBAC or ingress rule
- The impact you assess (e.g. privilege escalation, exposed endpoint, data exposure)
- Your assessment of severity
- Whether you have already disclosed this elsewhere

---

## Response timeline

| Stage                                  | Target                                            |
| -------------------------------------- | ------------------------------------------------- |
| Acknowledgement                        | Within 72 hours of receipt                        |
| Initial triage and severity assessment | Within 5 business days                            |
| Fix or mitigation published            | Depends on severity (see below)                   |
| Public disclosure                      | After fix is available, coordinated with reporter |

**Severity guidelines:**

- **Critical** (CVSS ≥ 9.0): fix targeted within 7 days
- **High** (CVSS 7.0–8.9): fix targeted within 14 days
- **Medium / Low**: addressed in the next scheduled release

We will credit reporters in release notes unless you request anonymity.

---

## Scope

This policy covers this repository's Kubernetes manifests and the ArgoCD
sync that applies them. It does not cover:

- **The workload itself** — report application vulnerabilities against
  [paruff/python-fawkes-path](https://github.com/paruff/python-fawkes-path).
- **Third-party container images** referenced by `deployment.yaml`. Report
  upstream vulnerabilities to the image's project; we bump tags when upstream
  patches are available.
- **ArgoCD, Kubernetes and the cluster itself** — report upstream
  vulnerabilities to those projects.
- **The rest of the Fawkes suite** — each repo carries its own security policy.

---

## Known constraints

**Everything merged here reaches the cluster.** ArgoCD syncs `main`
continuously, so resource limits, replicas, ingress rules, RBAC
(`serviceaccount.yaml`) and the image tag all take effect without a manual
deploy step. Treat every PR as production-reaching and review it accordingly.

**The image tag is machine-managed.** `deployment.yaml`'s image tag is bumped
by python-fawkes-path's CI through a pull request. Do not hand-edit it; do
review those automated PRs — a compromised pipeline would land here first.

**No secrets belong in this repo.** The manifests reference a service account
and a service monitor only. Credentials belong in the cluster's secret store,
never in these files.
