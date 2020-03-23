# simple-website-docker
A vanilla docker setup for a website.

## Local
### Setup
To setup locally, you must setup the frontend and backend separately and install the necessary components. For the frontend and backend setup, read the `README.md` files in their respective directories `frontend` and `backend`.

### Running
Once you successfully start the Node server and the backend server, head to `http://localhost:8080`.

## Docker
### Setup
The easiest way to run the whole system is through Docker and Docker Compose.

Install [Docker for Mac](https://docs.docker.com/docker-for-mac/install/) or [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) and Docker Compose should be included. You should be able to run
```bash
docker -v && docker-compose -v
```
and output should be similar to
```bash
Docker version 19.03.2, build 6a30dfc
docker-compose version 1.24.1, build 4667896b
```

Docker Compose automatically runs the `web` and `server` services that are defined in the `docker-compose.yml`.
1. `server` - Backend server
3. `web` - Frontend server that allows clients to interface with the backend

There are actually two YAML files that can be used with `docker-compose`: `docker-compose.prod.yml` and `docker-compose.local.yml`
- `docker-compose.prod.yml` is used on the production server
- `docker-compose.local.yml` is used for local development - main difference is no service is needed for a reverse-proxy and CertBot since everything is local

### Local Development and Deployment
To run the system using `docker-compose`, run in the project root
```bash
docker-compose -f docker-compose.local.yml up --build
```

To stop the system, use
```bash
docker-compose down
```

Now, head to `http://localhost:8080`.

## Remote Server Development and Deployment
To deploy the production system on a server, run
```bash
docker-compose -f docker-compose.prod.yml up --build
```

