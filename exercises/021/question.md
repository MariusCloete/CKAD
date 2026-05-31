# Question 21: Build a container image for a Node.js app

You have a Node.js app with `package.json` and `application.js`.

Create a `Dockerfile` with these requirements:

- Use base image `node:18-alpine`.
- Set working directory to `/app`.
- Copy dependency files first, then install dependencies.
- Copy the rest of the application files.
- Start the app with `npm start`.

Build the image with tag `myregistry.local:5000/ckad-node:1.0`.

