# Gestione dei certificati TLS con Rancher

Rancher permette di gestire certificati TLS per i servizi esposti tramite ingress controller (es. NGINX, Traefik) e per la sicurezza della dashboard stessa.

## Esempio di Secret TLS per Ingress

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: demo-tls
  namespace: default
  labels:
    app: hello-world
  annotations:
    cert-manager.io/issuer: "letsencrypt-prod"
type: kubernetes.io/tls
data:
  tls.crt: <base64-cert>
  tls.key: <base64-key>
```

## Utilizzo del certificato in un Ingress

```yaml
spec:
  tls:
  - hosts:
    - hello.local
    secretName: demo-tls
```

## Gestione tramite Rancher
1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Cluster Explorer** > **Secrets** per creare/importare certificati.
3. Puoi usare cert-manager per automatizzare la generazione e il rinnovo dei certificati.
4. Associa il secret TLS agli ingress tramite la UI o YAML.

## Note
- Puoi gestire certificati self-signed o Let's Encrypt.
- Rancher consente anche la gestione centralizzata dei certificati per la dashboard e le API.

---
Per dettagli: [Rancher TLS & Cert-Manager](https://rancher.com/docs/rancher/v2.6/en/security/cert-manager/)
