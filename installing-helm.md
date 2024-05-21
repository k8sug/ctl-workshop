# Installing HELM

## What is helm?

Helm is often referred to as the 'app store' for Kubernetes, offering a powerful and flexible way to manage Kubernetes applications. Helm Charts help you define, install, and upgrade even the most complex Kubernetes application, streamlining the deployment process.

{% hint style="info" %}
Learn more about Helm: [https://helm.sh/](https://helm.sh/)
{% endhint %}



We are using Play-With-Kubernetes on CentOS and running Kubernetes v1.27.2

The kubernetes repository for 1.27 have been deprecaded since early 2024.

{% hint style="info" %}
more info at: [https://kubernetes.io/blog/2023/08/31/legacy-package-repository-deprecation/](https://kubernetes.io/blog/2023/08/31/legacy-package-repository-deprecation/)
{% endhint %}

And it is beyond this workshop scope to uptade to the latest version.

### Install  OpenSSL on the Master Node

```
yum --disablerepo=kubernetes  install openssl -y
```

### Install HELM the Master Node

{% code overflow="wrap" %}
```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
{% endcode %}

Check that HELM is installed:

```
helm version
```

