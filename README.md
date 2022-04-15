## This is a production grade gitops with fluxcd with more than a cluser on AKS


# Deploy services for azure kubernetes infrastructure

```
After Deploying ARM template will use script create-cluster.sh to create the cluster from cluster services template 
and modify create-cluster.sh line 31 and 52 for the correct path for repo working directory 

ARM Template: https://github.com/EngMohamedElEmam/Azure-ARM-Template

```

# Then will use bash from Jumpbserver to run the following 
```
root@K8s-master:/#  ./setup/create-cluster.sh --aks-cluster-name aks-dev-elemam-01 --aks-nodes-resource-group 
aks-dev-elemam-nodes-01 --dns-hostname elemamm.developers.global.io --dns-resource-group Azure-DNS 
--letsencrypt-contact-email mohamed.elemam.hussin@gmail.com
```

# Complete sealed secrets configurations

```

After deploying the cluster will need the master key for sealed secret to be deployed will found it in 
/common/setup/sealed-secrets-master.key

root@K8s-master:/# kubectl apply -f sealed-secrets-master.key
```

# Note: How to check for master key 
```
root@K8s-master:/# kubectl get secret -n kube-system -l sealedsecrets.bitnami.com/sealed-secrets-key -o yaml 
```