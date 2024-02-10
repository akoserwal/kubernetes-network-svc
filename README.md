# kubernetes-network-svc

By default, there are two Pods handling the DNS work. The DNS service is available for servicing any DNS translation request:

 `kubectl get rs,pods -n kube-system -l k8s-app=kube-dns`

 The default implementation for DNS used to be a project called kube-dns, which has since been deprecated and substituted with coredns. 

`kubectl describe endpoints -n kube-system -l k8s-app=kube-dns`

kubectl get endpoints