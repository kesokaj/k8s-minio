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
    MINIO_SECRET_KEY: "3k0pLugg3n"
    MINIO_DOMAIN: "s3.spgo.se"

# If you edit in 1-secrets you also need to edit ingressroute.yaml
root@k8s:~/k8s-minio# cat ingressroute.yaml
---
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: s3-spgo-se
spec:
  entryPoints:
    - websecure
  routes:
  - match: Host(`*.s3.spgo.se`)
    kind: Rule
    services:
    - name: minio-s3
      port: 9000
  tls:
    certResolver: default
    domains:
    - main: s3.spgo.se
      sans:
      - '*.s3.spgo.se'

# When ready run in folder and wait for deployment to finish
kubectl apply -f .


########################################
WHEN DEPLOYMENT IS UP RUN BELOW COMMANDS
########################################


# Add server to mc list
mc alias set local https://s3.spgo.se superuser '3k0pLugg3n'

# List settings
mc alias list

# Add console user
mc admin user add local console '3k0pLugg3n'

# Create console adminpolicy
mc admin policy add local consoleAdmin consoleAdmin.json

# Set policy to console user
mc admin policy set local consoleAdmin user=console


````
