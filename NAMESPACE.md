# Gestione dei namespaces e multi-tenancy con Rancher

Rancher facilita la gestione di ambienti multi-tenant tramite la creazione e l'isolamento dei namespaces Kubernetes.

## Esempio di creazione Namespace

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: demo-namespace
```

## Assegnare risorse a un Namespace

Aggiungi il campo `namespace: demo-namespace` nei manifest YAML di deployment, service, ecc.

## Gestione tramite Rancher
1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Cluster Explorer** > **Projects/Namespaces**.
3. Crea un nuovo namespace o project.
4. Puoi assegnare ruoli e policy RBAC specifiche per ogni namespace/project.

## Note
- I namespaces permettono isolamento logico tra ambienti (dev, test, prod) o team diversi.
- Rancher consente anche la gestione di risorse, quote e limiti per namespace.

---
Per dettagli: [Rancher Projects & Namespaces](https://rancher.com/docs/rancher/v2.6/en/cluster-admin/projects-namespaces/)
