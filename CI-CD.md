# Esempio di pipeline CI/CD con Rancher e GitHub Actions

Questo esempio mostra come automatizzare il deploy su un cluster Kubernetes gestito da Rancher usando GitHub Actions.

## Esempio di workflow `.github/workflows/deploy.yaml`

```yaml
name: Deploy to Rancher Kubernetes

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Kubeconfig
        run: |
          mkdir -p $HOME/.kube
          echo "$KUBECONFIG_DATA" | base64 -d > $HOME/.kube/config
        env:
          KUBECONFIG_DATA: ${{ secrets.KUBECONFIG_DATA }}
      - name: Deploy hello-world
        run: |
          kubectl apply -f k8s/hello-world.yaml
          kubectl apply -f k8s/hello-world-ingress.yaml
```

## Come funziona
- Il workflow si attiva su ogni push su `main`.
- Usa un secret GitHub (`KUBECONFIG_DATA`) per accedere al cluster Rancher.
- Applica i manifest YAML tramite `kubectl`.

## Note
- Puoi generare il kubeconfig da Rancher e salvarlo come secret su GitHub.
- Puoi estendere la pipeline per includere test, build immagini Docker, ecc.

---
Per dettagli: [Deploy su Kubernetes con GitHub Actions](https://docs.github.com/en/actions/deployment/deploying-to-your-cloud-provider/deploying-to-kubernetes)
