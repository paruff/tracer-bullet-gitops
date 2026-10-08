## What This PR Does

<!-- One sentence. -->

## Closes

<!-- Issue number(s): Closes #N -->

---

## AI-Assisted Review Block

<!-- REQUIRED. Complete before requesting review. Use Copilot or your AI agent to help fill this in. -->
<!-- DORA 2025 (REVIEW-01): Structured review blocks reduce review time by making context explicit. -->

**What does this PR do in one sentence?**

<!-- Ask Copilot: "Summarise this diff in one sentence for a PR description" -->

**What are the top 2–3 failure modes?**

<!-- Ask Copilot: "What could this manifest change break once ArgoCD syncs it?" -->

**What tests cover this change?**

<!-- List the rendered-manifest or validation command you ran (e.g. `kustomize build .`). If none: explain why. -->

**Architecture check:**

<!-- Ask Copilot: "Does this diff stay declarative — no imperative commands, no hidden state?" -->

- [ ] No secrets, tokens, or credentials in any changed file (use the cluster's Secret, never a literal)
- [ ] No `:latest` tags — image references are pinned (digest or explicit version)
- [ ] `kustomize build .` renders cleanly and the diff is what I intended
- [ ] Resource requests/limits are set on any new workload
- [ ] RBAC stays least-privilege (`ServiceAccount` / `Role` bindings touched only deliberately)

**What I was NOT sure about (flag for human review):**

<!-- Any judgment call, ambiguous requirement, or edge case you deferred to the reviewer. -->

---

## Checklist

- [ ] `kustomize build .` passes locally before requesting review
- [ ] PR is < 400 changed lines, OR `large-pr-approved` label has been applied by a human
- [ ] No secrets or credentials in any changed file
- [ ] `README.md` updated if a manifest's contract or sync behaviour changed
