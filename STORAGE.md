# Gestione storage persistente con Rancher

Rancher consente di gestire lo storage persistente per i workload Kubernetes tramite l'integrazione con diversi provider di storage (NFS, Longhorn, Ceph, cloud, ecc.).

## Esempio di PersistentVolumeClaim (PVC)

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: demo-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
  storageClassName: longhorn
```

## Come usare il PVC in un Deployment

Aggiungi la sezione `volumes` e `volumeMounts` nel deployment:

```yaml
      volumes:
      - name: demo-storage
        persistentVolumeClaim:
          claimName: demo-pvc
      containers:
      - name: ...
        # ...
        volumeMounts:
        - mountPath: /data
          name: demo-storage
```

## Abilitare Longhorn tramite Rancher
1. Accedi alla dashboard Rancher e seleziona il cluster.
2. Vai su **Apps & Marketplace** > **Charts**.
3. Cerca e installa il chart "Longhorn".
4. Dopo l'installazione, puoi creare PVC usando la StorageClass `longhorn`.

---
Per dettagli: [Rancher Storage Docs](https://rancher.com/docs/rancher/v2.6/en/storage/)
