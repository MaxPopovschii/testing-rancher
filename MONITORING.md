# Esempio di monitoraggio workload con Rancher

Rancher offre funzionalità di monitoraggio integrate per i workload Kubernetes tramite Prometheus e Grafana.

## Abilitare il monitoraggio su Rancher

1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Apps & Marketplace** > **Charts**.
3. Cerca e installa il chart "Monitoring" (Prometheus + Grafana).
4. Segui la procedura guidata per configurare il monitoraggio del cluster e dei workload.

## Visualizzare le metriche

- Dopo l'installazione, accedi a **Cluster Explorer** > **Monitoring** per vedere le metriche di sistema e dei workload.
- Puoi accedere a Grafana direttamente dalla UI Rancher per dashboard avanzate.

## Esempio di alert

Puoi configurare alert personalizzati (ad esempio, su CPU o memoria) tramite la sezione **Alerts & Notifiers** di Rancher.

---
Per dettagli: [Rancher Monitoring Docs](https://rancher.com/docs/rancher/v2.6/en/monitoring-alerting/)
