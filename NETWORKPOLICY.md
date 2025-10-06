# Sicurezza avanzata: Network Policies con Rancher

Rancher permette di gestire la sicurezza di rete tra i pod tramite le Network Policies di Kubernetes.

## Esempio di NetworkPolicy

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: allow-only-namespace
  namespace: demo-namespace
spec:
  podSelector: {}
  policyTypes:
  - Ingress
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          name: demo-namespace
```

Questa policy consente il traffico in ingresso ai pod solo da altri pod nello stesso namespace.

## Gestione tramite Rancher
1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Cluster Explorer** > **Network Policies**.
3. Crea o importa una nuova NetworkPolicy YAML.

## Note
- Le Network Policies richiedono un CNI compatibile (es. Calico).
- Puoi definire regole granulari per traffico tra pod, namespace o IP.

---
Per dettagli: [Rancher Network Policies](https://rancher.com/docs/rancher/v2.6/en/network-policies/)
