# Question 22: Modify an image to run as non-root

Create a `Dockerfile` for a small Alpine-based utility container with these requirements:

- Use `alpine:3.20`.
- Install `curl`.
- Create user `appuser` with uid `1001`.
- Run the container as `appuser`.
- Set default command to `sleep 3600`.

Build the image with tag `myregistry.local:5000/alpine-tool:1.0`.

