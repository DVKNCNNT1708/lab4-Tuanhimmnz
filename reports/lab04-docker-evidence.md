# Lab 04 Docker Evidence

Generated locally on 2026-06-09. Repository evidence is pushed to GitHub; container image registry push depends on Docker registry login.

## Image Build

```text
docker build --progress=plain -t fit4110/iot-ingestion:lab04 .
Result: success
Image: fit4110/iot-ingestion:lab04 1424ad616e8c 273MB
```

## Runtime Health

```text
docker run -d --rm --name fit4110-iot-lab04 -p 8000:8000 --env-file .env.example fit4110/iot-ingestion:lab04
curl /health: {"status":"ok","service":"iot-ingestion","version":"0.4.0"}
Docker HEALTHCHECK: healthy
```

## Non-root User

```text
docker exec fit4110-iot-lab04 id
uid=100(appuser) gid=101(appgroup) groups=101(appgroup)
```

## Newman Result

```text
npm run test:local
requests: 11 executed, 0 failed
assertions: 19 executed, 0 failed
reports/newman-lab04-local.xml
reports/newman-lab04-local.html
```

## Image Tag

```text
docker tag fit4110/iot-ingestion:lab04 ghcr.io/dvkncnnt1708/team-iot:v0.1.0-team-iot
```
