### Sahip (Owner) Görev Listesi — velia.com.tr (MVP)

Bu dosya, kurulum ve operasyon sırasında size düşen adımları özetler.

#### Alan Adı & DNS
- `velia.com.tr` için A/AAAA → Cloudflare veya GCP Load Balancer IP
- `api.velia.com.tr` CNAME → API Gateway/Cloud Run URL (custom domain)
- `assets.velia.com.tr` CNAME → R2/S3 public domain (opsiyonel)

#### Firebase/GCP
- Firestore etkinleştir (native mode), bölge: `europe-west1`
- Service Account oluştur, `FIREBASE_CLIENT_EMAIL` ve `FIREBASE_PRIVATE_KEY` değerlerini `.env` içine gir
- IAM: Cloud Run Invoker, Pub/Sub Publisher/Subscriber, KMS CryptoKey Encrypter/Decrypter izinleri
- Pub/Sub topic’leri oluştur: `job.created`, `scene.generated`, ... (bkz. worker-events)

#### Depolama (R2/S3)
- `velia-assets` ve `velia-renders` bucket’larını oluştur
- Access key/secret üret ve `.env` içine gir
- Lifecycle: renders 14 gün hot, sonrası arşiv

#### Dış Servisler
- Banana API key ve model key
- ElevenLabs API key
- GPT-mini/small API key (QA)
- YouTube OAuth (Console’da): Client ID/Secret + Redirect URI `https://velia.com.tr/api/channels/youtube/connect`

#### Stripe
- Ürün/Plan oluştur (Pro 120 kredi)
- Price ID’yi `.env` → `STRIPE_PRICE_PRO`
- Webhook endpoint: `https://api.velia.com.tr/api/auth/stripe/webhook` ve `STRIPE_WEBHOOK_SECRET`

#### Gözlemlenebilirlik
- Sentry DSN oluştur ve `.env` içine gir
- Log sink: GCP Log Explorer uyarıları (E2E p95>10dk, fail>%8, regen>%30)

#### Güvenlik
- KMS key oluştur (env: `KMS_KEY_RESOURCE`) ve OAuth token şifreleme için kullan
- JWT secret belirle
- Cloudflare WAF temel kuralları, bot koruma

#### Yayın & Kota
- YouTube API quota monitor (dailyLimitExceeded durumunda erteleme testleri)
- “indir & manuel yükle” fallback akışı için kılavuz

#### Operasyonel Rutinler
- Haftalık kredi mutabakatı (ledger agregasyon)
- Arşiv & temizlik job’larının raporu (housekeeping)
- Preset whitelist güncellemesi (moderasyon)

