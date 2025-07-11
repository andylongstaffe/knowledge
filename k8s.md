## configure sso

Long version:
```
> aws configure sso
> aws sts get-caller-identity --profile <name>
# This retrieves necc credentials and cluster config and updates your kubeConfig file with the new cluster context
> aws eks update-kubeconfig --region us-east-1 --name <cluster-name> --profile <profile-name> --role-arn <role-arn>
> kubectl config get-contexts
> kubectl get namespaces 
# rename context
> kubectl config rename-context <context-name> <short-name>
```

Short version:
```
aws configure sso
aws sts get-caller-identity --profile <name>
aws eks update-kubeconfig --region us-east-1 --name <cluster-name> --profile <name> --role-arn <role-arn>
kubectl config rename-context  <context-name> <short-name>
```

Connect to EKS Cluster 

```
aws eks --profile qa list-clusters
aws eks update-kubeconfig --region us-east-1 --name <cluster-name> --profile qa && chmod 600 ~/.kube/config
aws --profile qa sts get-caller-identity
kubectl get ns
kubectl config rename-context <context-name> qa
kubectl get ns
kubectl config set-context --current --namespace=<namespace>
```

Cluster connections are sensitive to the tool versioning, namely kubectl client has to be very close to cluster version and definitely not higher if possible. AWS cli version can also be significant.

## Viewing/changing env vars

    kubectl edit deployment/compliance-engine -n <namespace>
Beware: saving changes to this file will cause restart of service and changes applied

## Changing envs

Kubectx/Kubens - GitHub - ahmetb/kubectx: Faster way to switch between clusters and namespaces in kubectl 

```
kubectx dev=arn:aws:eks:us-east-1:700386920060:cluster/cbc-dev-eks-cluster-v1
kubectx dev
kubens 
```

## Port forwarding

    kubectl port-forward service/<name> 3005:3005 -n qa

Kubefwd

    sudo kubefwd svc -n qa

## Misc

```
kubectl version
kubectl get pods -n qa
kubectl get svc -n qa
kubectl get pod pod-name -n qa -o yaml
kubectl logs -f service/compliance-engine
```

## Scaling/Deployments


```
-- scale down a service
kubectl -n cbc-sbx4 scale deploy compliance-engine --replicas=0
-- restart a service
kubectl -n cbc-dev rollout restart deployment compliance-engine
-- info
kubectl describe deployments compliance-engine
```

Login to container
```
kubectl -n dev exec --stdin --tty `kubectl  -n dev get pods   | grep compliance-engine | grep -v migrate | cut -d " " -f1` -- /bin/sh
```
