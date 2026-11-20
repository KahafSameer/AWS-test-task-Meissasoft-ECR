# AWS Test Task: NestJS on Amazon ECR

A minimal NestJS API, containerized with Docker, used to practice building an image and pushing it to **Amazon ECR**.

## Tech Stack

NestJS 11 · TypeScript · Node.js 18 (Docker image) · Jest · ESLint/Prettier

## API

| Method | Path | Response |
|---|---|---|
| `GET` | `/` | `Hello World!` |

The server listens on `PORT` (default `3000`).

## Prerequisites

- Node.js and npm, **or** Docker
- For ECR: the AWS CLI, configured with permissions to push to an ECR repository

## Run locally

```bash
git clone https://github.com/KahafSameer/AWS-test-task-Meissasoft-ECR.git
cd AWS-test-task-Meissasoft-ECR
npm install
npm run start:dev      # http://localhost:3000
```

## Run with Docker

```bash
docker build -t nest-word .
docker run -p 3000:3000 nest-word
```

## Push the image to Amazon ECR

```bash
aws ecr get-login-password --region <region> | docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com
docker tag nest-word:latest <account-id>.dkr.ecr.<region>.amazonaws.com/<repository>:latest
docker push <account-id>.dkr.ecr.<region>.amazonaws.com/<repository>:latest
```

## Scripts

| Command | Description |
|---|---|
| `npm run start` / `start:dev` / `start:debug` | Run the app (normal / watch / debug) |
| `npm run build` | Compile to `dist/` |
| `npm run start:prod` | Run the compiled app (`node dist/main`) |
| `npm run lint` / `npm run format` | ESLint / Prettier |
| `npm test` / `test:e2e` / `test:cov` | Unit / e2e / coverage tests |
