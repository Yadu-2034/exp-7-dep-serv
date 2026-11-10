python-deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: python-web-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: python-web
  template:
    metadata:
      labels:
        app: python-web
    spec:
      containers:
      - name: python-web
        image: dockersamples/flaskapp:latest
        ports:
        - containerPort: 5000


python-service.yaml


apiVersion: v1
kind: Service
metadata:
  name: python-web-service
spec:
  type: NodePort
  selector:
    app: python-web
  ports:
  - protocol: TCP
    port: 5000
    targetPort: 5000

