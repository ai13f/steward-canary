# steward-canary (gitops)

The GitOps repo of the image steward's selftest canary. `steward selftest` (in `ai13f/k8s-image-steward`) rewrites
`config/namespaces/steward-canary/` to each case's baseline, then lets the real steward pipeline open, judge,
merge or refuse, sync and roll back a PR here. Argo application `steward-canary` (`argo/application.yaml`, manual
sync) deploys it to namespace `steward-canary`. The upstream is `ai13f/steward-canary-src`. Nothing here is secret.

`status-overlay.yaml` is the canary's custom patch, the same pattern as the Dispatcharr overlays: a ConfigMap
subPath-mounted over `/app/app/status.py`.
