# Getting Started with Docker

We have a simple Nodejs app built using less than 10 lines.

We are going to containerise this app into a Docker Container. 

## Resources & Requirements

- Simple Nodejs & Express App
- [Official Node Image](https://hub.docker.com/_/node/)
- [Get Started Docker](https://www.docker.com/get-started)
- Docker Desktop
- VSCode & Official Docker Extension
- [Learn Docker in 7 Easy Steps - Full Beginner's Tutorial](https://youtu.be/gAkwW2tuIqE)

## Quickstart

1. Clone this repo ```gh repo clone cloudbrilliant/cuddly-chainsaw```
2. Run ```npm i``` to install express
3. Run & test the app locally ```npm start```
4. Local test url http://localhost:8080

## Dockerfile

Dockerfile is required in order to create image/container version of your app.

```Dockerfile
FROM node:14

WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm install

COPY . .

ENV PORT=8080

EXPOSE 8080

CMD ["npm", "start"]
```

## Docker Build

Build an image from a Dockerfile

the ```-t``` flag tags our image. Think of this simply as a human-readable name for the final image. Since we named the image getting-started, we can refer to that image when we run a container.

The ```.``` at the end of the docker build command tells that Docker should look for the Dockerfile in the current directory.

```bash
 docker build -t getting-started/demoapp:1.0 . 
```

[Build Reference](https://docs.docker.com/engine/reference/commandline/build)

## Docker Run

Run the command below to start your new image / container

The ```-p``` command maps the container port to a local port, in our case this opens up https://localhost:3000

```bash
docker run -p 3000:8080 getting-started/demoapp:1.0
```

[Run Reference](https://docs.docker.com/engine/reference/commandline/run)


