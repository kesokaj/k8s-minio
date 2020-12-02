##     
````
helm repo add minio https://helm.min.io/
helm install --namespace minio --name minio-s3 minio/minio --set persistence.size=8Gi --set mode=distributed --set replicas=2
````
