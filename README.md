## label-controller
Trivial Kubernetes controller for adding Pod labels.  
  
## Controller development
Controller in Go will add a `pod-name` label to pods that have a specific annotation.  

- Use Operator SDK and scaffold the repo as if developing Operator. Opeartor will contain a single controller. 
`operator-sdk init --domain=jkosik --repo=github.com/jkosik/k8s-label-controller`

`main.go` was created. Note: when developing [Helm-based Operator](https://github.com/jkosik/k8s-nginx-operator), no Go files were created.  

- We will also not need any CRDs since, Controller will handle existing resource - Pod. Initialize Controller code:
`operator-sdk create api --group=core --version=v1 --kind=Pod --controller=true --resource=false` creates `controllers/pod_controller.go`

We now have a new file: controllers/pod_controller.go. This file contains a PodReconciler type with two methods:
- Method `Reconcile` implements our logic.
- Method `SetupWithManager` called when Operator starts and executes reconciliation.

Details documented here: https://kubernetes.io/blog/2021/06/21/writing-a-controller-for-pod-labels/.

WIP...to be finished...