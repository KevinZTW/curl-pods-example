# Example to use curl in a Pod to retrieve all Pods information

This repository provides an example of how to create a Kubernetes pod with the necessary permissions to list other pods within the `default` namespace.


## Usage

1. To create a pod and grant the pod access to list pods and create the pod itself, apply the Kubernetes configurations provided in `curl-pod.yaml`:
```sh
   kubectl apply -f curl-pod.yaml
```

2. Execute Shell and Make a Request:

```sh
    kubectl exec -it curl-pod -- sh 
    curl -k -H "Authorization: Bearer $(cat /var/run/secrets/kubernetes.io/serviceaccount/token)" https://kubernetes.default.svc/api/v1/namespaces/default/pods
```