# testing-rancher

## Esempio di utilizzo Rancher per il deployment di un'applicazione su Kubernetes

Questo repository contiene un esempio pratico per dimostrare l'utilizzo di Rancher nella gestione di workload su Kubernetes.

### 1. Prerequisiti
- Un cluster Kubernetes gestito tramite Rancher
- Accesso all'interfaccia Rancher (web UI)

### 2. Deployment di una semplice applicazione (hello-world)

Nella cartella `k8s/` trovi:
- `hello-world.yaml`: Deployment di esempio (nginxdemos/hello) e Service
- `hello-world-ingress.yaml`: Esempio di Ingress per esporre il servizio all'esterno

#### Passi per il deploy tramite Rancher:
1. Accedi alla dashboard Rancher e seleziona il cluster desiderato.
2. Vai su **Workloads** > **Deploy** > **Import YAML**.
3. Carica il file `k8s/hello-world.yaml` oppure copia e incolla il contenuto.
4. Applica la configurazione.
5. Verifica che il workload sia attivo e il servizio creato.

#### Aggiunta di un Ingress tramite Rancher:
1. Vai su **Service Discovery** > **Ingresses** > **Import YAML**.
2. Carica il file `k8s/hello-world-ingress.yaml` oppure copia e incolla il contenuto.
3. Applica la configurazione.
4. Assicurati che l'Ingress Controller (es. NGINX) sia installato nel cluster.
5. Modifica il file hosts locali o il DNS per puntare `hello.local` all'IP del LoadBalancer/Ingress Controller.
6. Accedi a `http://hello.local` per vedere l'applicazione esposta tramite Ingress.

### 3. Esempio di gestione RBAC tramite Rancher

Nella cartella `k8s/` trovi anche il file `rbac-demo.yaml` che crea:
- Un ServiceAccount (`demo-user`)
- Un Role con permessi di sola lettura su pod e service
- Un RoleBinding che collega il ruolo all'utente

#### Passi per applicare la configurazione RBAC tramite Rancher:
1. Vai su **Cluster** > **Projects/Namespaces** > **Import YAML**.
2. Carica il file `k8s/rbac-demo.yaml` oppure copia e incolla il contenuto.
3. Applica la configurazione.
4. Verifica nella sezione **Security** > **Roles** e **Role Bindings** che le risorse siano state create.

### 13. Esempio di cluster per 25 microservizi

La cartella `k8s/` contiene una struttura pronta per ospitare 25 microservizi in un cluster Kubernetes gestito da Rancher:

- `namespaces/`: manifest per ambienti (dev, prod)
- `storage/`: StorageClass (Longhorn) e template PVC
- `microservices/`: template e esempio di deployment/service per ogni microservizio
- `ingress/`: esempio di Ingress per routing multiplo
- `rbac/`: esempio di RBAC per ambienti
- `networkpolicy/`: policy di sicurezza di default
- `monitoring/`, `backup/`, `cert-manager/`: guide e placeholder per installazione tramite Rancher

Per ogni microservizio, copia e personalizza il template in `microservices/microservice-template.yaml`.
Adatta l'Ingress per esporre ogni servizio con path dedicato.

Questa struttura è scalabile e segue le best practice Rancher/Kubernetes per ambienti enterprise.

---
Per approfondire: [Documentazione ufficiale Rancher](https://rancher.com/docs/)