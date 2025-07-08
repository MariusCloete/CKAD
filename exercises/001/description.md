#Question:
*You are given a simple Node.js application in the /app directory. Create a Dockerfile that:
- Uses the node:18-alpine base image
- Copies the application code into the container
- Installs dependencies
- Sets the default command to npm start
- Then, build the image with the tag myregistry.local:5000/myapp:latest and push it to the registry.
