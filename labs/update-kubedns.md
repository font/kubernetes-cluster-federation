# Update KubeDNS in each cluster with the Federation Config Map

Now that the federated cluster is up and ready, we need to update kube-dns in each cluster to specify the federation
domain name.

To update the kube-dns we will add a config map to the kube-dns namespace in each cluster specifying the federation
domain name.

## Prerequisites

### Store the GCP Project Name

```
export GCP_PROJECT=$(gcloud config list --format='value(core.project)')
```

### Replace federation zone name

Use the zone name you specified when creating the Google DNS Managed Zone.

```
sed 's/federation.com/YOUR_ZONE_NAME/' configmap/federation-cm.yaml > tmp && mv -f tmp configmap/federation-cm.yaml
```


## Create the Config Map

### gce-asia-east1

```
kubectl --context="gke_${GCP_PROJECT}_asia-east1-b_gce-asia-east1" \
  --namespace=kube-system \
  create -f configmap/federation-cm.yaml
```

```
kubectl --context="gke_${GCP_PROJECT}_asia-east1-b_gce-asia-east1" \
  --namespace=kube-system \
  get configmap kube-dns -o yaml
```

### gce-europe-west1

```
kubectl --context="gke_${GCP_PROJECT}_europe-west1-b_gce-europe-west1" \
  --namespace=kube-system \
  create -f configmap/federation-cm.yaml
```

```
kubectl --context="gke_${GCP_PROJECT}_europe-west1-b_gce-europe-west1" \
  --namespace=kube-system \
  get configmap kube-dns -o yaml
```

### gce-us-west1

```
kubectl --context="gke_${GCP_PROJECT}_us-west1-b_gce-us-west1" \
  --namespace=kube-system \
  create -f configmap/federation-cm.yaml
```

```
kubectl --context="gke_${GCP_PROJECT}_us-west1-b_gce-us-west1" \
  --namespace=kube-system \
  get configmap kube-dns -o yaml
```

### gce-us-central1

```
kubectl --context="gke_${GCP_PROJECT}_us-central1-b_gce-us-central1" \
  --namespace=kube-system \
  create -f configmap/federation-cm.yaml
```

```
kubectl --context="gke_${GCP_PROJECT}_us-central1-b_gce-us-central1" \
  --namespace=kube-system \
  get configmap kube-dns -o yaml
```

### gce-us-east1

```
kubectl --context="gke_${GCP_PROJECT}_us-east1-b_gce-us-east1" \
  --namespace=kube-system \
  create -f configmap/federation-cm.yaml
```

```
kubectl --context="gke_${GCP_PROJECT}_us-east1-b_gce-us-east1" \
  --namespace=kube-system \
  get configmap kube-dns -o yaml
```
