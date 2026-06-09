# RUN_LOCAL.md - Huong dan chay Lab 04

Tai lieu nay giup nguoi khac clone repo sach, build Docker image, chay container va kiem tra lai bang Newman trong 5 buoc.

## 1. Clone repo

```bash
git clone https://github.com/DVKNCNNT1708/lab4-Tuanhimmnz.git
cd lab4-Tuanhimmnz
```

## 2. Cai dependencies cho Newman/Prism/Spectral

```bash
npm ci
```

## 3. Build Docker image

```bash
docker build -t fit4110/iot-ingestion:lab04 .
```

## 4. Run container va kiem tra health

```bash
docker run --rm \
  --name fit4110-iot-lab04 \
  -p 8000:8000 \
  --env-file .env.example \
  fit4110/iot-ingestion:lab04
```

Mo terminal khac de kiem tra:

```bash
curl http://localhost:8000/health
```

Ket qua mong doi:

```json
{"status":"ok","service":"iot-ingestion","version":"0.4.0"}
```

## 5. Chay Newman tren container

```bash
npm run test:local
```

Report duoc sinh tai:

```text
reports/newman-lab04-local.xml
reports/newman-lab04-local.html
```

Ghi chu dung container:

```bash
docker stop fit4110-iot-lab04
```
