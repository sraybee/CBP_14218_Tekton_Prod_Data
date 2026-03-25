# CBP-14218: Production Tekton Data

**Purpose:** Cleanup old Tekton resources before v1.10.0 upgrade

**Collection Date:** March 24, 2026

---

## Quick Start for SRE

### Step 1: Verify Current State

Connect to the target cluster and run:

```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'

kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Compare output with `PROD_Data/CBP_14218_Query_Output.md`:**
- ✅ **Matches** → Proceed to Step 2
- ❌ **Differs** → Review differences, adapt cleanup commands accordingly

### Step 2: Execute Cleanup

Follow the instructions in **`PROD_Data/CBP_14218_SRE_Cleanup_Steps.md`**:
1. Check namespace status first
2. Choose correct cleanup method (A or B)
3. Verify cleanup completed

---

## Files in This Repository

| File | Description |
|------|-------------|
| `PROD_Data/CBP_14218_Query_Output.md` | Original query results from all 4 PROD clusters (March 24, 2026) |
| `PROD_Data/CBP_14218_SRE_Cleanup_Steps.md` | Step-by-step cleanup instructions for each cluster |

---

## Summary

**Total Resources Found:** 112 (1 TaskRun + 111 PipelineRuns)

| Cluster | TaskRuns | PipelineRuns | Total | Status |
|---------|----------|--------------|-------|--------|
| tekton-prod-us-west-2-gree | 0 | 2 | 2 | ⚠️ Needs cleanup |
| tekton-prod-us-west-2-blue | 0 | 0 | 0 | ✅ Already clean |
| tekton-prod-us-east-1-blue | 1 | 63 | 64 | ⚠️ Needs cleanup |
| tekton-prod-us-east-1-gree | 0 | 46 | 46 | ⚠️ Needs cleanup |

---

## Background

These resources contain the deprecated `DisableAffinityAssistant` feature flag from Tekton v0.62.9. They must be cleaned up before upgrading to Tekton v1.10.0.

**Queries executed on March 24, 2026:**

```bash
# TaskRuns with old flag
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'

# PipelineRuns with old flag
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```
