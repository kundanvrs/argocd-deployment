
## 🔴 Step 1: install 

```bash
kubectl create namespace argocd
```

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argocd/stable/manifests/install.yaml
```

---

## ⏳ Step 2: Wait until ready

```bash
kubectl get pods -n argocd
```

Wait until **ALL pods are**:

```text
Running (1/1 or 2/2)
```


## 🔑 Step 3: Get password

```bash
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 --decode
```

## 🌐 Step 4: Port forward (use safe port)

```bash
kubectl port-forward svc/argocd-server -n argocd 9090:443
```

---

## 🔐 Step 5: Login

Open:

```text
https://localhost:9090
```

* Username: `admin`
* Password: (from step 4)
