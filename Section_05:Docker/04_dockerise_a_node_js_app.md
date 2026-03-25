# 🐳 Guided Lab: Dockerfile from Scratch to Container

Welcome to your first Docker project lab.

In this lab, you will learn how to:
- Build a Node.js application
- Create a Docker image
- Run and manage containers
- Work like in a real DevOps workflow

---

## 📦 Part 1: Project Setup (Node.js App)

Let’s start by building our application structure manually — just like you’d do in a realworkspace.

### Step 1.1: Create project folder

```bash
mkdir my-app
cd my-app
```

### Step 1.2: Create package.json

```bash
touch package.json
```

paste the following inside:

```bash
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  }
}
```

### Step 1.3: Create server.js

```bash
touch server.js
```
paste:

```bash

const http = require('http');
const PORT = 3000;

http.createServer((req, res) => {
  res.writeHead(200, { 'Content-Type': 'text/plain' });
  res.end('Hello from inside a Docker container!\n');
}).listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
```

### Step 1.4: Create the Dockerfile

```bash
touch Dockerfile
```
Then add:

```bash
FROM node:18

WORKDIR /app

COPY package.json .
RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

At this point, your structure should look like:

```bash
my-app/
├── Dockerfile
├── package.json
└── server.js
```
## 📦 Part 2: Build the Docker Image

Let’s now create a Docker image from this codebase.

### Step 2.1: Build image

```bash
docker build -t my-node-app .
```
Docker will go through each instruction in the Dockerfile, creating intermediate imagelayers.

### Useful options

 - --no-cache – skip layer caching:

```bash
docker build --no-cache -t my-node-app .
```
 - -f – build using a Dockerfile in a different location:

```bash
docker build -t my-node-app -f Dockerfile.prod .
```

## Step 2.2: Verify image

```bash
docker images
```

## Step 2.3: Inspect image deeply

```bash
docker inspect my-node-app
```
This reveals configuration, layers, and even the default CMD that runs.

## 🚀 Part 3: Run the Container

Now that we’ve built the image, let’s bring it to life.

### Step 3.1: Start container

```bash
docker run -d -p 3000:3000 --name my-app-container my-node-app
```

## **What just happened?**
- -d : Detached mode (runs in background)
- -p : Maps host port to container port
- --name : Assigns a container name

## Step 3.2: Check running containers

```bash
docker ps
```

## Step 3.3: Test application

Open in browser:

```bash
http://localhost:3000
```

👉 Output:

```bash
Hello from inside a Docker container!
```

## ⚙️ Part 4: Common Docker Commands

Action	Command
List running containers: docker ps
List all containers	docker:  ps -a
Stop container:	docker stop my-app-container
Start container:	docker start my-app-container
Restart container:	docker restart my-app-container
Remove container:	docker rm my-app-container
Remove image:	docker rmi my-node-app

## 🧪 Part 5: Debugging & Inspection

View logs

```bash
docker logs my-app-container
```

Execute commands inside the container

```bash
docker exec -it my-app-container sh
```

or for ubuntu bases images

```bash
docker exec -it my-app-container bash
```

Once inside, try:

```bash
ls -al /app
cat server.js
```

then Exit:

```bash
exit
```

Monitor container

```bash
docker stats my-app-container
```

## 🧹 Part 6: Clean Up (Optional)

After testing clean up your environment: 

```bash
docker stop my-app-container
docker rm my-app-container
docker rmi my-node-app
```

### 🎯 What I Learned

- Built a Node.js application
- built a Docker image
- Ran a container with port mapping
- Managed and debugged containers using CLI


