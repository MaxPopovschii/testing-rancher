# Aggiornamenti e gestione delle versioni dei cluster con Rancher

Rancher permette di gestire facilmente gli aggiornamenti (upgrade) dei cluster Kubernetes e delle applicazioni.

## Aggiornamento del cluster Kubernetes
1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Cluster Management** > **Clusters**.
3. Seleziona il cluster e clicca su **Edit/Upgrade**.
4. Scegli la versione di Kubernetes desiderata e avvia l'upgrade.

## Aggiornamento delle applicazioni (workload)
- Puoi aggiornare i manifest YAML e riapplicarli tramite Rancher (UI o import YAML).
- Rancher supporta anche il rolling update automatico dei workload.

## Note
- Prima di aggiornare, verifica la compatibilità delle versioni e considera di eseguire un backup.
- Rancher mostra lo stato di avanzamento e i log dell'upgrade.

---
Per dettagli: [Rancher Cluster Upgrades](https://rancher.com/docs/rancher/v2.6/en/cluster-admin/cluster-upgrades/)
