
```bash
docker build -t myregistry.local:5000/myapp:latest .
```
```bash
docker push myregistry.local:5000/myapp:latest
```
```bash
kubectl run --image myregistry.local:5000/myapp:latest
```
