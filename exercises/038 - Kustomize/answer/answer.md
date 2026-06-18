Apply the Kustomize base:

```bash
mkdir -p kustomize-app/base
cd kustomize-app/base/
k create service clusterip kustom-web --tcp=80:80 --dry-run=client -o yaml > service.yaml
k create deployment kustom-web --image=nginx:1.27 --port=80 --dry-run=client -o yaml > deployment.yaml
cat > kustomization.yaml <<EOF
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization

resources:
  - deployment.yaml
  - service.yaml
EOF
```
```
kubectl apply -k .
kubectl get deploy kustom-web
kubectl get svc kustom-web
```

