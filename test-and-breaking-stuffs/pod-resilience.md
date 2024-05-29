---
description: Observe Kubernetes' automatic recovery by deleting the backend pod
---

# 🧑‍⚕️ Pod Resilience

get the back end pod name:

```
kubectl get pod
```

Delete it

```
kubectl delete pod <pod-name>
```

Check the pods again

```
kubectl get pod
```

Interact with the frontend and see the reposnse comming from the new backend pod

