# HIDTCOP local deploy setup with docker-compose

HIDTCOP full stack installation and setup with docker-compose. 

For cloud configuration, navigate towards [Cloud Configuration section](## Cloud Configuration).

For gitpod configuration, navigate to [Gitpod Configuration](## Gitpod configuration).

## Cloud Configuration

Read [DEPLOY.md](./DEPLOY.md).

## Gitpod Configuration

Open a new workspace with this repository.

```
$ docker-compose up -d
```

Open the prompt browser tab for port 5433.

Login with default credential (check configuration on docker-compose.yml).

Add new server with hostname "db", username "postgres" & passsword "postgres".

You can configure your own custom credentials on environment settings in docker-compose.yml

## Requirements

Install [docker](https://docs.docker.com/get-docker/).

Install [docker-compose](https://docs.docker.com/compose/install/).

## Installation

Git clone HIDTCOPHospitalApi repository:
```bash
git clone https://github.com/thamardaw/HIDTCOPStackDeploy.git
```

Change directory into the cloned repository:

```bash
cd HIDTCOPStackDeploy
```

## Pull docker images

Pull docker images:

```bash
docker-compose pull
```

## Run docker containers

Run the pulled images:

```bash
docker-compose up -d
```

## Configuration

The react front end can be accessed at "http://localhost" or "http://127.0.0.1".

The api can be accessed at "http://localhost:8000".

The database can be accessed at "http://localhost:5432".

If you wish to change any configuration, you can change them inside [docker-compose.yml](./docker-compose.yml) file.

**Make sure the ports 80, 8000 and 5432 are not used by another service.**

**PS: Don't change api url and port because react can't access the api variable at run time.**
