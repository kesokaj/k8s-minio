##     
````
helm repo add minio https://helm.min.io/
helm install --namespace minio minio-s3 minio/minio --set persistence.size=8Gi --set mode=distributed --set replicas=2

or run the yaml files


handle new users and such

https://www.civo.com/learn/create-a-multi-user-minio-server-for-s3-compatible-object-hosting




.\mc.exe alias set s3-vks https://s3.vks.vmar.se <admin key> <admin pass>
.\mc.exe admin user add s3-vks <anv> <lösenord>
.\mc.exe admin policy add s3-vks test policy.json
.\mc.exe admin policy set s3-vks test user=vmarsimon

````
