# New Marketplace Demo

New Marketplace mor/lila temalı, çok satıcılı B2C marketplace demosudur. Bu çalışma gerçek bir müşteri brief'inden değil, sentetik kapsam ve sınırları zorlama testinden üretilmiştir. Amaç dolu görünen bir demo sunmak, kaynak kodu teslim etmek ve ileride teknik ekibin dashboard, entegrasyon ve production servislerini genişletebilmesini sağlamaktır.

İngilizce ana dokümantasyon için [README.md](./README.md) dosyasına bakın.

## Kapsam

- Kampanya slider'ı, kategori navigasyonu, arama, sıralama, favori, karşılaştırma, ayrı ürün detay URL'leri, sepet ve sandbox checkout içeren müşteri vitrini.
- `public/demo-products` altında tutulan 12 adet lokal PNG demo ürün görseli.
- Marketplace metrikleri, rol sınırları, provider durumu, audit log ve PNG logo yükleme içeren admin dashboard.
- Katalog, stok, teslim tipi, performans, kampanya katılımı, komisyon ve hakediş görünürlüğü için satıcı dashboardları.
- Kampanya, banner, landing içerik, SEO/analytics mock durumu, yasaklı kelime moderasyonu ve PNG logo yükleme için marketing dashboardları.
- Ödeme providerları, fatura adapter durumu, iade, chargeback, satıcı hakedişi, komisyon ve mutabakat için finans dashboardları.
- Sipariş müdahale sınırı, iptal/iade, satıcıya soru, eskalasyon ve canlı destek durumu için destek dashboardları.
- Marketplace seed verisini dönen ve sandbox demo sipariş oluşturan lokal Express API.
- Varsayılan İngilizce arayüz ve Türkçe dil toggle'ı.

## Lokalde Çalıştırma

Gereksinimler:

- Node.js 20+ önerilir
- npm

```powershell
npm install
npm run dev
```

Varsayılan lokal adresler:

- Müşteri vitrini: `http://localhost:5173`
- API: `http://localhost:4000`
- Health check: `http://localhost:4000/api/health`

## Demo URL'leri

- `http://localhost:5173` - genel müşteri vitrini
- `http://localhost:5173/musteri` - müşteri vitrini alias
- `http://localhost:5173/lilabook-pro-14` - ürün detay sayfası örneği
- `http://localhost:5173/admin` - admin kontrol dashboardu
- `http://localhost:5173/satici1` - satıcı katalog ve stok senaryosu
- `http://localhost:5173/satici2` - satıcı performans ve hakediş senaryosu
- `http://localhost:5173/marketing1` - marketing kampanya senaryosu
- `http://localhost:5173/marketing2` - marketing SEO ve moderasyon senaryosu
- `http://localhost:5173/finans1` - finans ödeme ve iade senaryosu
- `http://localhost:5173/finans2` - finans hakediş ve mutabakat senaryosu
- `http://localhost:5173/destek1` - destek sipariş/iade senaryosu
- `http://localhost:5173/destek2` - destek canlı destek ve satıcıya soru senaryosu

Sol menüde yalnızca müşteri kategorileri görünür. Dashboard route'ları özellikle sadece direkt URL ile erişilecek şekilde bırakılmıştır.

## Build ve Doğrulama

```powershell
npm run lint
npm run build
```

Bu repoda Python runtime kullanılmaz; bu yüzden `requirements.txt` gerekmez.

## API Endpointleri

- `GET /api/health`: lokal API sağlık kontrolü.
- `GET /api/marketplace`: ürün, satıcı, sipariş, kampanya, provider ve audit seed verisi.
- `POST /api/orders/checkout`: sandbox demo sipariş oluşturur.

## Dil Desteği

Varsayılan arayüz dili İngilizcedir. Sol menüdeki dil toggle'ı müşteri vitrini ve dashboard arayüzünü Türkçeye geçirir. Lokalizasyon metinleri `src/i18n.ts` dosyasında tutulur.

## Logo Yükleme

Admin ve marketing dashboard kendi logolarını ayrı ayrı yükleyebilir.

- Kabul edilen dosya tipi: `image/png`
- Maksimum dosya boyutu: `512 KB`
- Davranış: yükle, önizle, değiştir, kaldır
- Saklama: demo için browser `localStorage`

## Demo Ürün Görselleri

Ürün kartları çalışma anında dış görsel URL'lerine bağlı kalmasın ve vitrin dolu görünsün diye lokal PNG demo görselleri kullanır. API seed verisi `public/demo-products` altındaki path'leri döner.

## Demo ve Production Sınırı

Bu repo bilinçli olarak demo teslimidir; production marketplace backend'i değildir.

- Ödeme: sandbox/mock
- Kargo: mock adapter
- E-fatura ve e-arşiv: mock adapter
- Analitik ve pixel: mock bağlı
- KVKK/GDPR, ticari ileti izni, production ödeme sözleşmeleri, production kargo sözleşmeleri, fatura entegrasyonları, observability ve güvenlik sertleştirmesi production teknik/hukuk ekipleri tarafından tamamlanmalıdır.

## Kaynak Kod Devir Notu

Genişletme için ana noktalar:

- `server/index.mjs`: ileride gerçek backend servislerine bağlanabilecek demo API sınırı.
- `src/api.ts`: frontend API adapter katmanı.
- `src/data.ts`: frontend tipleri ve fallback seed verisi.
- `src/i18n.ts`: İngilizce ve Türkçe arayüz metinleri.
- `src/App.tsx`: demo ekran akışları, route'lar, ürün detay davranışı ve dashboard etkileşimleri.
- `src/App.css`: responsive UI, mor/lila görsel sistem ve dashboard layout'u.

## Kabul Edilmiş Demo Riskleri

- Bu demo 10M/gün production ziyaretçi kapasitesini kanıtlamaz.
- Gerçek ödeme, kargo, fatura ve CRM entegrasyonları mock/sandbox olarak ayrılmıştır.
- Marketplace klonu production'da hukuki/IP riski taşıyabilir. Bu repo iş akışı ve UI demosu olarak teslim edilir.
- Gizlilik, güvenlik, auditability ve uyumluluk kontrolleri canlıya çıkmadan önce production review gerektirir.

## Güvenlik

Bu proje kapsamlı güvenlik protokollerini takip eder:
- **Dependabot:** Otomatik bağımlılık ve GitHub Actions güncellemeleri.
- **CodeQL:** Güvenlik açıklarını tespit etmek için Statik Uygulama Güvenlik Testi (SAST).
- **Güvenlik Politikası:** [SECURITY.md](./SECURITY.md) dosyasında tanımlanmıştır.
- **Proaktif Tarama:** CI süreçlerine entegre npm audit, secret scanning ve unsafe JS tespiti.

