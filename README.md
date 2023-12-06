##     
````
# Edit in file 1-secrets.yaml if desired
root@k8s:~/k8s-minio# cat 1-secrets.yaml
apiVersion: v1
kind: Secret
metadata:
  name: minio-s3-creds
type: Opaque
stringData:
    MINIO_ACCESS_KEY: "superadmin"
    MINIO_SECRET_KEY: "<SUPER SECRET KEY>"
    MINIO_DOMAIN: "<FQDN MINIO>"

# If you edit in 1-secrets you also need to edit ingressroute.yaml
# When ready run in folder and wait for deployment to finish
kubectl apply -f .


########################################
WHEN DEPLOYMENT IS UP RUN BELOW COMMANDS
########################################


# Add server to mc list
mc alias set local https://<FQDN MINIO> superuser '3k0pLugg3n'

# List settings
mc alias list

# Add console user
mc admin user add local console '3k0pLugg3n'

# Create console adminpolicy
mc admin policy add local consoleAdmin consoleAdmin.json

# Set policy to console user
mc admin policy set local consoleAdmin user=console


````
