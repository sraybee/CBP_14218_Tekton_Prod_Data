# CBP-14218: Production Tekton Data

**Purpose:** Cleanup old Tekton resources before v1.10.0 upgrade

**Collection Date:** March 24, 2026

---

## Queries Executed

We ran the following queries in each PROD Tekton cluster and prepared `CBP_14218_Query_Output.md`:

**Query 1 (TaskRuns):**
```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**Query 2 (PipelineRuns):**
```bash
kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

---

## Files

- **CBP_14218_Query_Output.md** - Query results from all 4 PROD clusters (112 resources found)
- **CBP_14218_SRE_Cleanup_Steps.md** - Cleanup commands cluster-wise

---

## Usage Instructions

### Before Running Cleanup Commands

**1. Verify Data Is Still Accurate:**

Run the same queries in the target cluster:

```bash
kubectl get taskruns -A -o json | jq -r '.items[] | select(.status.retriesStatus[0].provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'

kubectl get pipelineruns -A -o json | jq -r '.items[] | select(.status.provenance.featureFlags.DisableAffinityAssistant != null) | "\(.metadata.namespace) \(.metadata.name)"'
```

**2. Compare Results:**

- If output **matches** `CBP_14218_Query_Output.md` → Use `CBP_14218_SRE_Cleanup_Steps.md` directly
- If output **differs** → Adapt cleanup commands based on current data

### Running Cleanup

Use commands from `CBP_14218_SRE_Cleanup_Steps.md` for the target cluster.

---

## Summary

**Total Resources Found:** 112 (1 TaskRun + 111 PipelineRuns)

| Cluster | TaskRuns | PipelineRuns | Total |
|---------|----------|--------------|-------|
| tekton-prod-us-west-2-gree | 0 | 2 | 2 |
| tekton-prod-us-west-2-blue | 0 | 0 | 0 |
| tekton-prod-us-east-1-blue | 1 | 63 | 64 |
| tekton-prod-us-east-1-gree | 0 | 46 | 46 |
