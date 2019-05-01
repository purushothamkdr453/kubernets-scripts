#-------- Please run the following commands-------------

using Kubectl:
-------------------------

echo -n "admin" > username.txt
echo -n "password" > password.txt

kubectl create secret generic my-secret --from-file=username.txt --from-file=password.txt
sudo kubectl get secret
sudo kubectl describe secret my-secret

using manually:
----------------------------------
echo -n "admin" | base64 
output: YWRtaW4K
echo -n "password" | base64
output: cGFzc3dvcmQK

echo "YWRtaW4K" | base64 --decode
echo "cGFzc3dvcmQK" | base64 --decode
---------------------------------------------------------

sudo kubectl create -f my-secret.yaml
sudo kubectl get secrets -o yaml

sudo kubectl create -f secrets-using-volumes.yaml
sudo kubectl exec secrets-using-volumes ls /etc/foo/username
sudo kubectl exec secrets-using-volumes cat /etc/foo/username

sudo kubectl create -f secrets-using-env.yaml
sudo kubectl exec pod/secrets-using-environment-variables | grep SECRET
sudo kubectl exec -it secrets-using-environment-variables -- /bin/sh
then after entering into terminal run env which displays SECRET_USER_NAME, SECRET_PASSWORD env variables

