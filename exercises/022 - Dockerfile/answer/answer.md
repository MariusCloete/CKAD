Example build command:

```bash
docker build -t myregistry.local:5000/alpine-tool:1.0 -f Dockerfile .
```

Example run command:

```bash
docker run --rm myregistry.local:5000/alpine-tool:1.0 id
```

