This is the commands for demo

```
# install argo
kubectl create namespace argo-rollouts
kubectl apply -n argo-rollouts -f https://github.com/argoproj/argo-rollouts/releases/latest/download/install.yaml

# command to test against stable
curl -v http://ic-demo.local/

# command to test against canary
curl -v -H "x-canary: true" http://ic-demo.local/

# create name space
kubectl create ns ic-demo

#delete namespace
kubectl delete namespace ic-demo

# install app
helm install demo-nginx -n ic-demo argo-traffic-management-demo


# upgrade version by changing the design state
 helm upgrade demo-nginx -n ic-demo ./argo-traffic-management-demo


# upgrade version by changing the running state
kubectl argo rollouts set image demo-nginx demo-nginx=nginx:1.20.0 -n ic-demo
kubectl argo rollouts set image demo-nginx demo-nginx=nginx:1.19.1 -n ic-demo


# watch a rollout 
kubectl argo rollouts get rollout demo-nginx -n ic-demo --watch


# complete rollout
kubectl argo rollouts promote demo-nginx -n ic-demo
```