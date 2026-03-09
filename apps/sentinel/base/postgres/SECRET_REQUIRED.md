# Required Kubernetes Secret

This app expects a Secret in each environment namespace:

Name: sentinel-postgres-secret

Keys:
- POSTGRES_DB
- POSTGRES_USER
- POSTGRES_PASSWORD

Create it like this (example for dev):

kubectl -n sentinel-dev create secret generic sentinel-postgres-secret `
  --from-literal=POSTGRES_DB=sentinel `
  --from-literal=POSTGRES_USER=sentinel `
  --from-literal=POSTGRES_PASSWORD=sentinelpass `
  --dry-run=client -o yaml | kubectl apply -f -
