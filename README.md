# 🚀 **Kubernetes Deployment Guide**

> CBA K8S 클러스터를 새로 구축하거나 재배포할 때 사용하는 전체 적용 순서입니다.

---

## 🧭 전체 적용 순서


### 1️⃣ Namespace 생성
```bash
kubectl apply -f namespace.yaml
```

### 2️⃣ Cert-Manager ClusterIssuer 적용
```bash
kubectl apply -f cluster-issuer-letsencrypt.yaml
```

### 3️⃣ MySQL 스토리지 및 설정 적용
```bash
kubectl apply -f mysql/pv.yaml
kubectl apply -f mysql/pvc.yaml
kubectl apply -f mysql/configmap.yaml
kubectl apply -f mysql/secret.yaml
kubectl apply -f mysql/deployment.yaml
kubectl apply -f mysql/service.yaml
```

### 4️⃣ Redis 배포
```bash
kubectl apply -f redis/
```

### 5️⃣ CBA-WAS 배포
```bash
kubectl apply -f cba-was/secret.yaml
kubectl apply -f cba-was/
```

### 6️⃣ CBA-WS 배포
```bash
kubectl apply -f cba-ws/
```

### 7️⃣ 서비스 인그레스 설정
```bash
kubectl apply -f cba-connect/ingress.yaml
```

### 8️⃣ Grafana 인그레스 적용 (옵션)
```bash
kubectl apply -f grafana-ingress.yaml
```

---

**팁**: 여러 리소스를 한 번에 적용하려면 `kubectl apply -f <directory>/`를 사용하세요. 예: `kubectl apply -f redis/`.