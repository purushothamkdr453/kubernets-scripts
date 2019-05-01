#--- Execute the following commands-----------------

mkdir -p configure-pod-container/configmap/
wget https://k8s.io/examples/configmap/game.properties -O configure-pod-container/configmap/game.properties
wget https://k8s.io/examples/configmap/ui.properties -O configure-pod-container/configmap/ui.properties

# Create the configmap
kubectl create configmap game-config --from-file=configure-pod-container/configmap/

1.using directories which conatins config files:
----------------------------------------------
sudo kubectl create configmap game-config --from-file=configure-pod-container/configmap/
sudo kubectl get configmaps -o wide
sudo kubectl get configmaps game-config -o yaml

2. using files:
-------------------
curl -OL https://k8s.io/examples/pods/config/redis-config
sudo kubectl create configmap example-redis-config --from-file=redis-config
sudo kubectl get configmap example-redis-config

sudo kubectl create -f test-configmap-pod-using-volume-mounts.yaml

sudo kubectl exec redis cat /redis-master/redis.conf

sudo kubectl exec redis redis-cli
>> CONFIG GET maxmemory

3.using literals:
-----------------------------------------------------------
sudo kubectl create configmap special-configmap --from-literal=name=purushotham
sudo kubectl create -f test-configmap-pod-using-environment-variables.yaml
sudo kubectl logs pod-configmap-using-literals-environment-variables
