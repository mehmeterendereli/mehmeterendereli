### Admin Test Matrisi — Mekanizmalar ve Hata Yakalama

Tüm mekanizmalar admin panelinden tetiklenebilir olmalı. Aşağıdaki testler için UI’de “Test” butonları ve sonuç logları gereklidir.

#### 1) Kredi Ledger & Idempotency
- Test: `reserveCredits(6)` aynı anahtar ile 2 kez → toplam tek sefer düşmeli
- Test: `image -1`, `regen -1` toplam düşüm ve `refund +1` iade
- Negatif: yetersiz kredi → 409 ve no-op

#### 2) Slot Tetikleyici (Cron Simülasyonu)
- Test: TZ uyumlu slot eşleşmesi
- Negatif: YouTube bağlı değil → job oluşturma yok, bildirim gönderimi

#### 3) Banana (Image) Entegrasyonu
- Test: stub/real toggle; gecikme ölçümü
- Negatif: timeout → exponential backoff, 3 deneme sonra `scene.failed`

#### 4) QA Skoru & Re-Gen
- Test: skor <80 → max 3 re-gen, ledger düşümleri doğru
- Negatif: 3 denemede <80 → job `manual_review`, bildirim

#### 5) TTS
- Test: TTS fetch ve asset kaydı
- Negatif: 429 → jitter backoff, sonrasında no-op tekrarlar idempotent

#### 6) Render (ffmpeg)
- Test: 720p/1080p preset, aspect pad
- Negatif: eksik asset → `video.failed` ve otomatik `REFUND` yok (kural gereği)

#### 7) YouTube Upload & Schedule
- Test: planlı zamanlama, “unlisted” staging
- Negatif: `dailyLimitExceeded` → defer(nextSlot) ve banner

#### 8) Bildirimler (Web Push)
- Test: “Yayınlandı”, “Düzeltme bekliyor”, “Kredi %80”
- Negatif: abonelik yok → sessiz fail + audit log

#### 9) Güvenlik & Moderasyon
- Test: whitelist preset’lar geçer, riskli prompt blok
- Negatif: ünlü/marka/nefret/şiddet → fail fast, audit

#### 10) Gözlemlenebilirlik
- Test: structured log alanları (jobId, sceneIndex, step, attempt)
- Alarm: E2E p95>10dk, fail>%8, regen>%30 → uyarı düşer

