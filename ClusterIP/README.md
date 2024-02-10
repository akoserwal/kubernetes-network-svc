kubectl apply -f svc.yaml

`kubectl get svc`
`kubectl get services -o wide`

NAME             TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)   AGE
kubernetes       ClusterIP   10.96.0.1      <none>        443/TCP   7m5s
webapp-service   ClusterIP   10.96.91.121   <none>        80/TCP    5s

➜  ~ kubectl get endpoints
NAME             ENDPOINTS                     AGE
kubernetes       10.89.3.2:6443                8m15s
webapp-service   10.244.0.5:80,10.244.0.6:80   75s

The IPs listed are the virtual IPs of the Pods. The Service is also assigned a virtual IP. More details on the Service configuration and its connect endpoints can be viewed

kubectl describe svc/webapp-service


 ```kubectl run intra-cluster-curl --image=ellerbrock/alpine-bash-curl-ssl --rm -it --restart=Never -- bash -c "for i in {1..12}; do curl http://webapp-service:80; done"```

 `webapp-service.default.svc.cluster.local`

 ```kubectl run intra-cluster-curl --image=ellerbrock/alpine-bash-curl-ssl --rm -it --restart=Never -- bash -c "for i in {1..6}; do curl http://webapp-service.default.svc.cluster.local:80; done"```


 `kubectl apply -f svc-target.yaml`

 The application itself is still configured to listen on port 80, but the new access port from the ClusterIP is port 8080. Kubernetes Service manages the translation between the two port numbers.