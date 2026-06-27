# Bebek Uyutucum

Bebekler için uyku sesleri uygulaması. Beyaz gürültü, ninni, yağmur, kalp atışı ve daha fazlasıyla bebeğinizi rahatlatın.

**Android · Kotlin · Jetpack Compose · Media3 · DataStore · Play Billing · AdMob**

---

## Özellikler

- **51 rahatlatıcı ses** — beyaz gürültü, pembe gürültü, kahverengi gürültü, anne karnı, kalp atışı, ninni, yağmur, okyanus, rüzgar, vantilatör ve ev sesleri
- **Karıştırma** — birden fazla sesi aynı anda çalın (premium)
- **Zamanlayıcı** — otomatik kapanma
- **Ağlama algılama** — bebek ağladığında seçtiğiniz ses otomatik çalın (isteğe bağlı, cihaz üzerinde çalışır)
- **Uyku takibi** — rutinler ve istatistikler
- **Çevrimdışı** — tüm sesler cihazınızla gelir, internet gerekmez
- **10 dil** — Türkçe, İngilizce, Almanca, Fransızca, İspanyolca, Portekizce, Rusça, Arapça, Endonezyaca, Hintçe
- **Reklamsız ve satın almasız** — 1.0.0 sürümünde tamamen ücretsiz

---

## Teknoloji

- AGP 8.7.3, Kotlin 2.0.21, JDK 17
- Compose BOM 2024.12.01
- Media3 1.5.1 (ExoPlayer + MediaSession)
- DataStore Preferences 1.1.1
- Play Billing 8.0.0 (iskelet, devre dışı)
- Play Services Ads 24.4.0 (iskelet, devre dışı)
- UMP 3.0.0 (iskelet, devre dışı)

## Mimari

Single-module, MVVM. Hilt yok. Application-scoped controller'lar `App.instance` üzerinden.

---

## Build

```bash
cp local.properties.example local.properties
# local.properties'i düzenle (gerçek ID'ler opsiyonel)
./gradlew assembleDebug
./gradlew bundleRelease
```

## Yapı

- `app/src/main/java/bebebek/uykusesi/app/`
  - `core/` — common, design, navigation, permissions, ext
  - `data/` — DataStore, sound catalog, repository
  - `domain/` — modeller, use case'ler
  - `playback/` — MediaSessionService, controller, timer, fade
  - `ads/` — AdMob manager (devre dışı)
  - `billing/` — Play Billing manager (devre dışı)
  - `ui/` — Compose ekranları
- `app/src/main/res/` — 10 dilde strings, temalar, ikonlar
- `assets/licenses/audio_licenses.csv` — ses lisansları
- `store-listing/` — Play Store metinleri

## BuildConfig flag'leri (local.properties)

- `ad.enabled` — AdMob (varsayılan false)
- `billing.enabled` — Play Billing (varsayılan false)
- `ump.enabled` — UMP (varsayılan false)
- `crashlytics.enabled` — Crashlytics (varsayılan false)
- `ad.app.id`, `ad.banner.unit.id`, `ad.interstitial.unit.id`, `ad.rewarded.unit.id`
- `billing.lifetime.id`, `billing.monthly.id`, `billing.yearly.id`

---

## Gizlilik Politikası

**Son güncelleme:** 27 Haziran 2026

Bu gizlilik politikası, Bebek Uyutucum uygulamasının (bundan sonra “Uygulama”) verilerinizi nasıl işlediğini açıklar. Uygulamayı kullanarak bu politikayı kabul etmiş olursunuz.

### Kısa cevap

**Hiçbir kişisel veriniz toplanmaz.** Uygulama çevrimdışı çalışır, hesap istemez, reklam göstermez, analytics kullanmaz. Tüm tercihleriniz yalnızca kendi cihazınızda saklanır.

### 1. Toplanan veriler

#### Cihazınızda saklananlar (sunucuya gönderilmez)

| Veri | Neden saklanıyor |
|---|---|
| Dil ve tema tercihi | Uygulamayı seçtiğiniz dilde/görünümde açmak |
| Favori sesler | “Favorilerim” listesini göstermek |
| Son çalınan ses | Tekrar açtığınızda hızlı başlatmak |
| Zamanlayıcı ve ses seviyesi | Açılışta aynı ayarlarla devam etmek |
| Uyku geçmişi | Rutinler ekranında istatistik göstermek |
| Kurulum/onboarding durumu | Tekrar sormamak |

Bu veriler cihazınızın dışına asla çıkmaz.

#### Hiçbir zaman toplanmayan veriler

- Ad, e-posta, telefon, adres
- Konum
- Fotoğraf, video, mikrofon kaydı
- Kişi listesi, takvim, mesajlar
- Hesap veya şifre
- Sağlık verileri
- Reklam kimliği
- Çocuk verisi

### 2. Mikrofon ve ağlama algılama

Ağlama algılama özelliği **varsayılan olarak kapalıdır**. Açarsanız:

- Mikrofon yalnızca Uygulama açıkken ve özellik sizin tarafınızdan açıksa çalışır.
- Ses yalnızca anlık olarak analiz edilir; **kaydedilmez**, **saklanmaz**, **gönderilmez**.
- Cihazınızdan çıktığınızda veya özelliği kapattığınızda mikrofon hemen kapanır.

Mikrofon iznini reddederseniz Uygulamanın diğer özellikleri çalışmaya devam eder.

### 3. Reklam ve satın alma

Uygulamanın bu sürümünde **reklam yok** ve **uygulama içi satın alma yok**.

- AdMob kodu var ama devre dışı (`ENABLED = false`). Hiçbir reklam isteği gönderilmez.
- Play Billing altyapısı var ama aktif satın alma akışı yok.

İleride bunlar eklenirse bu sayfa güncellenir ve Uygulama içinde size bildirilir.

### 4. İnternet kullanımı

Uygulama temel olarak internetsiz çalışır. İnternet yalnızca Google Play Hizmetleri ile sınırlı teknik iletişim için kullanılır. Sizin adınıza bir veri gönderilmez.

### 5. Veri güvenliği

- Verileriniz cihazınızın korumalı uygulama alanında saklanır.
- Bulut yedekleme devre dışıdır (`allowBackup = false`). Verileriniz Google bulutuna yedeklenmez.
- Çökme kaydı yalnızca cihazınızda tutulur ve otomatik olarak hiçbir yere gönderilmez.

### 6. Verilerinizi silme

Verilerinizi silmek için herhangi birini yapın:

1. **Uygulama içinde:** Ayarlar → Yerel verileri sıfırla
2. **Uygulamayı kaldırın:** Tüm yerel veriler silinir
3. **Android Ayarlar:** Uygulamalar → Bebek Uyutucum → Depolama → Verileri temizle

Sunucuda veri olmadığı için bize ulaşmanız gerekmez; ama isterseniz aşağıdaki adresten iletişime geçebilirsiniz.

### 7. Çocuklar

Uygulama çocuklara yönelik değildir. Hedef kitle ebeveynler ve yetişkinlerdir. Çocuklardan veri toplanmaz. Uygulama bir tıbbi cihaz değildir; bebek güvenliği her zaman ebeveynin sorumluluğundadır.

### 8. Yasal haklarınız

GDPR (AB), KVKK (Türkiye) ve CCPA (California) kapsamında haklarınız vardır: erişim, düzeltme, silme, işlemeye itiraz.

Uygulama verileri yalnızca cihazınızda olduğu için bu hakları doğrudan kendiniz uygulayabilirsiniz (yukarıdaki silme yöntemleri). Sorularınız için iletişime geçebilirsiniz; 30 gün içinde yanıt veririz.

### 9. Değişiklikler

Bu politikayı zaman zaman güncelleyebiliriz. Önemli değişiklikler Uygulama içinde bildirilir. Bu sayfada yayınlandığı anda yürürlüğe girer.

### 10. İletişim

- **Geliştirici:** mattecnology
- **E-posta:** Uygulama içi Ayarlar → Hakkında bölümündeki adres
- **Bu politikanın adresi:** https://github.com/mattecnology/babysleeper/blob/main/privacy-policy.md

---

*Bu politika Bebek Uyutucum 1.0.0 sürümü için geçerlidir.*

---

## Önemli Notlar

- Bu uygulama tıbbi tavsiye değildir.
- Çocuklara yönelik değildir; ebeveyn aracıdır.
- Tüm ses dosyaları CC0 veya telif ücretsiz olmalıdır.
- `allowBackup = false`; `dataExtractionRules` minimum.
- Android 14+ için `foregroundServiceType="mediaPlayback"` zorunludur.

## Lisans

Tüm hakları saklıdır © 2026 mattechnology
