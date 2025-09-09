### Worker Event Payload Tipleri ve Idempotency Anahtarı

Bu belge, Pub/Sub olay şemalarını ve idempotency anahtarı formatını tanımlar. Tüm eventlerde `trace` alanı zorunludur.

#### Ortak Alanlar (Her Event)
- `trace.jobId` (string)
- `trace.sceneIndex` (integer | null)
- `trace.step` (string)
- `trace.attempt` (integer)
- `trace.idempotencyKey` (string) — Format: `{userId}:{jobId}:{step}:{sceneIndex}:{attempt}`
- `ts` (ISO datetime)

#### job.created
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": null, "step": "job.created", "attempt": 0, "idempotencyKey": "u_1:j_123:job.created:-:0"},
  "userId": "u_1",
  "projectId": "p_1",
  "sceneCount": 6,
  "computeMode": "economy"
}
```

#### scene.generated
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": 0, "step": "scene.generated", "attempt": 1, "idempotencyKey": "u_1:j_123:scene.generated:0:1"},
  "prompt": "...",
  "imageUrl": "https://.../scene_00.png",
  "costEstimate": 0.039
}
```

#### scene.qa_passed
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": 0, "step": "scene.qa_passed", "attempt": 1, "idempotencyKey": "u_1:j_123:scene.qa_passed:0:1"},
  "qaScore": 87
}
```

#### scene.tts_ready
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": 0, "step": "scene.tts_ready", "attempt": 1, "idempotencyKey": "u_1:j_123:scene.tts_ready:0:1"},
  "ttsUrl": "https://.../scene_00.wav"
}
```

#### video.render_ready
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": null, "step": "video.render_ready", "attempt": 0, "idempotencyKey": "u_1:j_123:video.render_ready:-:0"},
  "scenes": 6
}
```

#### video.rendered
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": null, "step": "video.rendered", "attempt": 0, "idempotencyKey": "u_1:j_123:video.rendered:-:0"},
  "videoUrl": "https://.../short_final.mp4",
  "resolution": "1080p"
}
```

#### video.scheduled
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": null, "step": "video.scheduled", "attempt": 0, "idempotencyKey": "u_1:j_123:video.scheduled:-:0"},
  "publishTime": "2025-09-09T13:00:00+03:00"
}
```

#### video.published
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": null, "step": "video.published", "attempt": 0, "idempotencyKey": "u_1:j_123:video.published:-:0"},
  "youtubeUrl": "https://youtube.com/watch?v=..."
}
```

#### video.failed
```json
{
  "trace": {"jobId": "j_123", "sceneIndex": 0, "step": "video.failed", "attempt": 3, "idempotencyKey": "u_1:j_123:video.failed:0:3"},
  "errorCode": "QA_LOW_SCORE",
  "errorMessage": "QA score < 80 after 3 attempts"
}
```

### Idempotency Kuralları
- Her worker girişinde `trace.idempotencyKey` zorunlu ve ledger işlemleri bu anahtarla tekil.
- Aynı anahtarla tekrar gelen event no-op olmalı; yan etkiler tekrarlanmaz.
- Ledger türleri: `RESERVE/-6`, `IMAGE/-1`, `REGEN/-1`, `REFUND/+1`, `RELEASE/+6`.

