---
description: Adjust replica counts to scale your deployment
---

# 📈 Scaling On-Demand

Get the deployments

```
kubectl get deploy
```

If you are on Azure increase the backend

```
kubectl edit deploy <deploy-name>
```

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Check the new pods

```
kubectl get pods
```



