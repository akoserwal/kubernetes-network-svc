 kubectl get services -o wide | grep -z '80:30080'

 ➜  ~  kubectl get services -o wide | grep -z '80:30080'
NAME             TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE     SELECTOR
kubernetes       ClusterIP   10.96.0.1      <none>        443/TCP        15m     <none>
webapp-service   NodePort    10.96.91.121   <none>        80:30080/TCP   8m31s   app=webapp


for i in {1..12}; do curl 172.18.144.5:30080; done