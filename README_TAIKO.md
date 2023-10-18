# Blockscout plan

1. Deploy blockscout all-in-one to local k8s cluster (check the deployment steps below)
2. Make sure it can serves the requirements below
3. Check how to do contributions upstream if requirements are not met currently

# Requirements

1. Custom stat tiles and time-based graphs -> could also move to another page
2. Custom labels for special addresses (SignalService, etc.)
3. Change validate to propose -> easy enough to introduce as an env var in blockscout
4. Extend the block view to include things like "Extra data"
5. Show burnt fees (should be able to also config in blockscout upstream)

# Local blockscout helm deployment steps

1. Make sure kubernetes is enabled in Docker Desktop settings + confirm with a `kubectl cluster-info`
2. Install prometheus to local kubernetes cluster:

```sh
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install [RELEASE_NAME] prometheus-community/kube-prometheus-stack
```

3. Install the local helm chart: `cd charts/blockscout-stack && helm install <release-name> .` (e.g., `helm install my-blockscout-release .`)
4. You can always look at running kubernetes pods with: `kubectl get pods`
5. You can always inspect logs of pods with `kubectl get logs -f <pod-name>` (e.g., this will complain about missing env vars)
6. You can upgrade the current helm deployment by updating the local `values.yaml` and running `helm upgrade <release-name> .`
