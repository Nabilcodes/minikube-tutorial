# minikube-tutorial

1.
Before deployment exposure as a service, the pod hello-node had the following logs

I0517 03:36:08.184065       1 log.go:195] Started HTTP server on port 8080

I0517 03:36:08.186187       1 log.go:195] Started UDP server on port  8081

After exposure, it has this following logs : 

I0517 03:36:08.184065       1 log.go:195] Started HTTP server on port 8080

I0517 03:36:08.186187       1 log.go:195] Started UDP server on port  8081

I0517 03:49:26.307512       1 log.go:195] GET /

I0517 03:49:26.543544       1 log.go:195] GET / 

The logs showed several addition of get request. Every time the app was opened,
the number of get request log increases by two.

2.
The purpose of the -n option was to specify namespace. The namespace specified 
in the command was kube-system, a namespace that was used to acommodate kube's system
components. Hence, with the kube-system namespace specified, only pods and services
belongs to the kube system will be displayed.

== ROLLING UPDATE ==

1. The difference between recreate deployment and rolling update strategy lies in how
the changes from old deployment to new ones executed. In rolling update strategy, the
old deployments were shut down and replaced gradually. During the changes, the new
deployments incrementally were added. While in the recreate deployments, all of the old
deployments were shut down simulataneously, and changed to new deployments also simulatenously.

2. In recreate deployment strategy, i do the following steps :
- export config
- change the strategy type in deployment.yaml to recreate
- shut down kubernetes
- start kubernetes cluster and apply the config files 

4. Using manifest files, starting a kubernetes cluster with specific desired configurations
was easier with less steps. These mechanism enables safer set-up process which is naturally
prone to human error. During my experience in deploying app manually, many things need to
be checked continually, and a lot of data may appear and increasing cognitive complexity.
