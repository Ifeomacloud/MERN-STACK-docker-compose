# A simple MERN stack application 

This is a simple MERN (MongoDB, Express.js, React, Node.js) stack application. Below are the instructions for running the application both with Docker Compose and without Docker.

## Run it locally without Docker

## Prerequisites

- Install **npm** on your machine.

## Start server

- *cd mern/server*
- *npm install*
- *npm start*

## Start Client
- *cd mern/client*
- *npm install*
- *npm run dev*

### Create a network for the docker containers

- *docker network create mern_network*

### Build the client 


- *cd mern/frontend*
- *docker build -t frontend .*


### Run the client

- *docker run --name=frontend --network=mern_network -d -p 5173:5173 frontend*

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Run the mongodb container

- *docker run --network=mern_network --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest*

### Build the server


- *cd mern/backend*
- *docker build -t backend .*


### Run the server 

- *docker run --name=backend --network=mern_network -d -p 5050:5050 backend*

## Using Docker Compose

- *docker compose up -d*

## Stopping the Docker Compose

- *docker compose down*

