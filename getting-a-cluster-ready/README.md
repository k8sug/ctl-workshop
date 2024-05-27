# 🎡 Getting a Cluster Ready

## Options Available:

### [1 - Azure (30 days free trial)](./#id-1-azure)

It is free for 30 days for new accounts, but a valid Credit or Debit card number is required.\
Great environment and quite resouceful VMs.

### [2 - Killercoda - Kubernetes Playgroud (free version available)](./#id-2-killercoda)

It is totally free, with the limitation to 60 minutes sessions. Also it is quite limited on resources. max of 4GB of RAM and only one Node. Pros: have the latest version of the most used applications and Kubernetes 1.30





## 1: Azure

{% embed url="https://azure.microsoft.com/en-us/free" %}

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

User a existing Microsoft/Hotmail/Skype/Github account or create a new one.

<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

After signup you will be redirect to portal.azure.com

{% embed url="https://portal.azure.com/#home" %}

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

You will be given an important choice: Bash or PowerShell

<figure><img src="../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>Go with Bash</p></figcaption></figure>

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

Select the Azure Subscription and click in Apply, it will give you a terminal.\


<figure><img src="../.gitbook/assets/image (13).png" alt=""><figcaption><p>Switch to Bash if you have select PowerShell</p></figcaption></figure>

```
// Copy this repository
git clone https://github.com/yongkanghe/aks-casa.git;cd aks-casa
```

```
// Automation to spin-up a cluster
./aks-deploy.sh
```

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

## 2: Killercoda

{% embed url="https://killercoda.com/playgrounds/course/kubernetes-playgrounds/one-node-4GB" %}

Sign-in using a Github, Gitlab, Google or Email.

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

It will provide a Node with 4gb.

<figure><img src="../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

You can click and reduce the slide menu.&#x20;

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

And if you click in Editor, it will provide an VSCode like enviroment.

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>
