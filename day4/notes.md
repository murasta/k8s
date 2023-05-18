kubectl create configmap configuration --from-file=./ -o yaml --dry-run=client

kubectl create cm python-api --from-env-file=fromenv -o yaml --dry-run=client > cm.yaml

kubectl create configmap python-api-cm --from-literal=LOG_LEVEL=INFO --from-literal=REDIS_HOST=redis-service -o yaml --dry-run=client > cm.yaml


https://demo.178.128.138.47.sslip.io/api/v1/info



apiVersion: apps/v1
kind: Deployment
metadata:
  name: python
  labels:
    projekt: python
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 2
  replicas: 3
  revisionHistoryLimit: 0
  selector:
    matchLabels:
      app: python
  template:
    metadata:
      labels:
        app: python
        projekt: python
    spec:
      containers:
      - name: python
        image: krajewskim/python-api:new
        resources: {}
        ports:
          - containerPort: 5002
            name: api
        livenessProbe:
          tcpSocket:
            port: api
        readinessProbe:
          httpGet:
            path: /healthz
            port: api
        envFrom:
          - configMapRef:
              name: python-api-cm
        env:
          - name: Maciek
            value: test
      affinity:
        podAntiAffinity:
          preferredDuringSchedulingIgnoredDuringExecution:
          - weight: 100
            podAffinityTerm:
              labelSelector:
                matchExpressions:
                - key: app
                  operator: In
                  values:
                  - python
              topologyKey: "kubernetes.io/hostname"



kubectl delete all,pv,pvc,cm,ingress --all



https://cloud.google.com/blog/products/databases/to-run-or-not-to-run-a-database-on-kubernetes-what-to-consider



kubectl create secret docker-registry regcred --docker-server=https://index.docker.io/v1/ --docker-username=krajewskim --docker-password=dckr_pat_o7pJ-S_-Ea0fzLb5NJcc33A4j14 --docker-email=maciejkra@gmail.com


https://github.com/knaopel/docker-frontend-backend-db/tree/master


krajewskim/backend

krajewskim/frontend



kubectl delete all,pv,pvc,cm,ingress,secrets --all


/app/.env.development
REACT_APP_API_URL=http://api.127.0.0.1.nip.io/api  #node internal ip #~kubectl get nodes -o wide

