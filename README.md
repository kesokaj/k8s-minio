##     
````
helm repo add minio https://helm.min.io/
helm install --namespace minio --generate-name minio/minio --set persistence.size=32Gi
````
