# Secrets-Token-kubernetes-Version-

Summarization of secrets,sa on kubernetes version
**V1.20 and below**
when a service account is created, it automatically generates a secret and token. This token is utilized by all pods, as the secret is precisely mounted within each pod. However, this setup poses security risks, as all tokens and secrets are identical across pods. Scaling the pods for testing purposes confirms this uniformity. Consequently, the secret, serving as a long-lived credential, is mounted to every pod in the deployment. Hence, when integrating the token into JWT, its expiration is not evident.
**V1.21 to V1.23**
After creating service account ,it crate secret automatically but they dont use and that secret is useless. Created secret was not mounted in the pod. All of these pods are using project volume(V1.21 and upwards version) and it short-lived (for 1 hr ) and so that it enhances security purpose. 
**V.124 and above **
After creating service account ,it not create secret anymore.

Note: start from V1.21 to onwards - kubelet is a process and run on inside of every nodes. kubelet from worker nodes are requested to kube-api from control plane to get the token for pods.

Check out in detail.... https://www.notion.so/17-2-24-Secret-c75f698e23a34a5ea9ff9a130a0736a9?pvs=4

![Screenshot 2024-03-01 at 10 44 36 PM](https://github.com/GritworkTMH/Secrets-Token-kubernetes-Version-/assets/142704734/ad618fb1-9b53-49a7-8ae5-de599cb2ffc7)
![Untitled](https://github.com/GritworkTMH/Secrets-Token-kubernetes-Version-/assets/142704734/dc0ca8d9-9244-400c-80ef-5cc5de4bb052)

