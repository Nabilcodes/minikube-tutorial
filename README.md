# minikube-tutorial

1. Before deployment exposure as a service, the pod hello-node had the following logs ;
I0517 03:36:08.184065       1 log.go:195] Started HTTP server on port 8080
I0517 03:36:08.186187       1 log.go:195] Started UDP server on port  8081

After exposure, it has this following logs : 
I0517 03:36:08.184065       1 log.go:195] Started HTTP server on port 8080
I0517 03:36:08.186187       1 log.go:195] Started UDP server on port  8081
I0517 03:49:26.307512       1 log.go:195] GET /
I0517 03:49:26.543544       1 log.go:195] GET / 

The logs showed several addition of get request. Every time the app was opened,
the number of get request log increases by two.

2. The purpose of the -n option was to specify namespace. The namespace specified 
in the command was kube-system, a namespace that was used to acommodate kube's system
components. Hence, with the kube-system namespace specified, only pods and services
belongs to the kube system will be displayed.
