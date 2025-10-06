# Backup e Disaster Recovery con Rancher

Rancher supporta il backup e il ripristino dei cluster Kubernetes tramite l'integrazione con Velero.

## Esempio di backup con Velero

### 1. Installazione di Velero tramite Rancher
- Accedi alla dashboard Rancher e seleziona il cluster.
- Vai su **Apps & Marketplace** > **Charts**.
- Cerca e installa il chart "Velero".
- Configura il backend di storage (es. S3, NFS, Azure Blob, ecc.).

### 2. Eseguire un backup
- Dopo l'installazione, vai su **Cluster Explorer** > **Velero** > **Backups**.
- Crea un nuovo backup scegliendo namespace, risorse e policy desiderate.

### 3. Ripristino di un backup
- Sempre dalla sezione **Velero**, seleziona il backup da ripristinare e avvia il restore.

## Note
- Puoi schedulare backup automatici e configurare la retention.
- I backup possono essere esportati e importati tra cluster diversi.

---
Per dettagli: [Rancher Backup & Restore](https://rancher.com/docs/rancher/v2.6/en/backups/)
