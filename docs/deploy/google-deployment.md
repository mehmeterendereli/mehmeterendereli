### Google Cloud Deployment Guide — Including Render Pipeline

Target: App (Next API), workers (Cloud Run), orchestration (Pub/Sub), data (Firestore), storage (R2/S3) for MVP.

#### Architecture Placement
- Region: europe-west1
- Cloud Run services: api-gateway, worker-story, worker-image, worker-qa, worker-tts, worker-render, worker-youtube, worker-housekeeping
- Pub/Sub topics and pull subscriptions
- Firestore (Native mode)
- R2/S3 externals (signed URL)

#### CI/CD
- Cloud Build or GitHub Actions to Cloud Run deploy
- Use Secret Manager or KMS-backed secrets

#### Environment Variables
- Use .env.example as reference; in prod, prefer Secret Manager

#### Render Path (worker-render)
- Cloud Run CPU-only is sufficient; bundle static ffmpeg binary in the image
- Input: scene_*.png, narration.wav, music.mp3 (signed GET)
- Output: short_final.mp4 (signed PUT)
- ffmpeg filter chain matches SDD sample (scale 1080x1920, pad, amix)

#### Quotas and Scaling
- Max concurrency 1-2 for render and TTS
- Pro parallelism: up to 3 jobs concurrently (queue throttle)
- Pub/Sub retry: exponential backoff, maxDeliveryAttempts ~16

#### Security
- Service-to-service IAM: least privilege invoker
- KMS for OAuth token encryption; minimize secret surface
- Optional VPC egress and egress IP pinning

#### Observability
- Sentry DSN; structured logs: jobId, sceneIndex, step, attempt
- Metrics aggregation into metrics_daily (avgE2E, failRate, regenRate, costPerVideo)

#### Operations
- Housekeeping: archive after 14 days, poison queue cleanup
- Quota alerts for YouTube daily limits and backoff

