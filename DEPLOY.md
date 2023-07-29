To set up the full web frontend and api from scratch, follow the steps described below.

## Requirements

Install [docker](https://docs.docker.com/get-docker/).

Install [docker-compose](https://docs.docker.com/compose/install/).

## Set up HIDTCOP Hospital Web

Clone HIDTCOPHospitalWeb repository

```bash
git clone https://github.com/thamardaw/HIDTCOPHospitalWeb.git
```

Change directory into cloned repository

```bash
cd HIDTCOPHospitalWeb
```

Build docker image

```bash
docker build -t hidtcophospitalweb:latest \
--build-arg="BASE_URL=<localhost or host ip>:8000" \
--build-arg="THEME=#03C0C1" \
--build-arg="TITLE=Dagon Lin" \
--build-arg="TITLE_SHORT=DGL" \
--build-arg="TITLE_LONG=Dagon Lin Hospital" \
.
```

## Set up HIDTCOP Hospital API

Clone HIDTCOPHospitalApi repository

```bash
git clone https://github.com/thamardaw/HIDTCOPHospitalApi.git
```

Change directory into cloned repository

```bash
cd HIDTCOPHospitalApi
```

Build docker image

```bash
docker build -t hidtcophospitalapi:latest .
```

## Configuration

Some configurations need to be changed on docker-compose.yml to pick up the built images.

docker-compose.yml

```
client:
    container_name: client
    image: hidtcophospitalweb:latest (from jasoniv/hidtcophospitalweblocal:latest)
```

```
backend:
    container_name: backend
    image: hidtcophospitalapi:latest (from jasoniv/hidtcophospitalapi:latest)
```

## Usage

Run docker compose

```bash
docker compose up -d 
```

Access web portal at http://localhost:3000

## Stop or delete the service

```
docker compose down
```

## Cloud Configuration

Specify the host ip when buiding web image

```
docker build -t hidtcophospitalweb:latest \
--build-arg="BASE_URL=3.144.5.47:8000" \
--build-arg="THEME=#03C0C1" \
--build-arg="TITLE=Dagon Lin" \
--build-arg="TITLE_SHORT=DGL" \
--build-arg="TITLE_LONG=Dagon Lin Hospital" \
.
```

Allow necessary firewall rule (below configuration is for ubuntu os)

```
sudo ufw allow 3000
sudo ufw allow 8000
```

**note:** 3000 \& 8000 allowed because they are the default ports in docker-compose.yml, change according to configuration if modified

**important:** Do not allow postgrest port 5432 because we do not want to expose our database to public internet

Web portal will finally up on http://3.144.5.47:3000
