sudo kubectl get pods -o wide
sudo kubectl exec volume-hostpath df /test-mnt
sudo kubectl exec volume-hostpath -- /bin/sh
cd /test-mnt
echo "From pod" > from_pod.txt
on the node go to ls /test-vol1 then you should be able to find file created above
delete the pod manually and make sure the hostPath volume still exists even after deleting the pod
kubectl delete pod volume-hostpath

