# HIDTCOP local deploy setup with docker-compose

HIDTCOP full stack installation and setup with docker-compose.

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

The api can be accessed at "http://localhost:8000".

The database can be accessed at "http://localhost:5432".

If you wish to change any configuration, you can change them inside [docker-compose.yml](./docker-compose.yml) file.

**PS: Don't change api url and port because react can't access the api variable at run time.**
