# kubernetes-examples

`kubectl -n default port-forward $(kubectl -n default get pod -l name=nginx-pod -o jsonpath='{.items[0].metadata.name}') 8080:80 & open http://localhost:8080/`

`kubernetes get po` - for listing all pods running inside a cluster  
`kubernetes get deploy` - for listing all deployments resources running inside a cluster

[Kubernetes Cheat Sheet](https://github.com/sureshsubbaiah/kubernetes-examples/blob/master/Kubernetes%20Cheat%20Sheet.pdf)
