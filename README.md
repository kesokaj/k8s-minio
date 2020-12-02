##     
````
helm repo add minio https://helm.min.io/
helm install --namespace minio minio-s3 minio/minio --set persistence.size=8Gi --set mode=distributed --set replicas=2

or run the yaml files


handle new users and such

https://www.civo.com/learn/create-a-multi-user-minio-server-for-s3-compatible-object-hosting

````
