#--- Execute the following commands
kubectl get pods -o wide
kubectl describe pod test-ed
kubectl exec test-ed df /cache
kubectl delete pod test-ed
