# Kind with ciluim

Guide: https://docs.cilium.io/en/stable/installation/kind/

`helm repo add cilium https://helm.cilium.io/`

`docker pull quay.io/cilium/cilium:v1.15.0`

```
helm install cilium cilium/cilium --version 1.15.0 \
   --namespace kube-system \
   --set image.pullPolicy=IfNotPresent \
   --set ipam.mode=kubernetes
```

`kubectl get pods -n kube-system`

# Verify cilium

`kubectl create ns cilium-test`

`kubectl apply -n cilium-test -f https://raw.githubusercontent.com/cilium/cilium/1.15.0/examples/kubernetes/connectivity-check/connectivity-check.yaml`

# Clean up
kubectl delete ns cilium-test