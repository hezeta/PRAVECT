# MiniDesk — Deney ve bağımsız karşılaştırma

**Yayın durumu:** Kısmi değerlendirme · **Deney:** 13–15 Ekim 2026 kayıtları · **Karşılaştırma:** 15 Ekim 2026, Linux/Python 3.13.5 ikincil sınaması

**Kısaca:** Aynı hedeflerden iki çalışır MiniDesk uygulaması üretildi. Ortak testlerin çoğu başarılı olsa da gerçek tarayıcı, hedef Windows ortamı ve güvenilir performans ölçümleri tamamlanamadı. Bu nedenle karşılaştırma kesin bir kazanan göstermiyor.

Bu sayfa, PRAVECT'in önceki adı **AI Engineer** ile gerçekleştirilen üretim deneyini ve aynı gereksinimlerden geliştirilmiş iki MiniDesk yazılımını birlikte özetler. Ayrıntılar dört belgede, seçilmiş sonuçlar `evidence/selected/` altında bulunur. **Bu çalışma yeni PRAVECT eklentisinin doğrulandığı veya üretim yöntemlerinden birinin üstünlüğünün kanıtlandığı anlamına gelmez.**

## Amaç ve iki çalışma

MiniDesk, tek bilgisayarda çalışan, talepleri oluşturup düzenleyen, durumunu değiştiren, filtreleyen, geçmişini tutan ve JSON dışa aktarımı sunan yerel bir uygulamadır. İki ürün aynı [gereksinim belgesine](minidesk/evidence/selected/ROADMAP.md) dayanır:

- **A — AI Engineer kullanılan üretim:** Python/Flask ve SQLite. Başlangıç 2.1.1-rc.1 tabanlıdır; üretim sırasında `phasefix.1` ve `attestfix.1` düzeltmeleri uygulanmıştır.
- **B — referans üretim:** AI Engineer kullanılmadan, Python standart `http.server` ve SQLite ile geliştirilmiştir.

A üretiminde Codex kod ve sınama yardımcılarını geliştirmiş; insan operatör imza ve bağımsız inceleme aşamalarında yer almıştır. Bu, gözetimsiz bir ajan deneyi değildir. M0–M4 kabul kayıtları vardır; son raporlanan aday `cand-c9989cb5fa78c893` kimliğini taşır. Süreçte 311 komut kaydedilmiştir, fakat bu sayı veya komut süreleri tek başına token tüketimini, etkin çalışma süresini ya da AI Engineer'ın getirdiği yükü vermez. [Yöntem ve süreç](minidesk/methodology.md).

## Ortak karşılaştırmanın kısa sonucu

| Ölçüt | A — AI Engineer kullanılan | B — referans |
|---|---:|---:|
| Ürünlerin kendi testleri | 59/59 PASS | 38/38 PASS |
| Önceden belirlenen ortak senaryolar | 48 | 48 |
| PASS | 31 | 32 |
| FAIL | 1 | 0 |
| BLOCKED | 11 | 11 |
| NOT_ASSESSED | 4 | 4 |
| NOT_APPLICABLE | 1 | 1 |
| Python ifade kapsamı | %98,57 (276/280) | %93,37 (310/332) |
| Genel 100 puanlık sonuç | Hesaplanmadı | Hesaplanmadı |

**A'nın tek ortak FAIL sonucu**, özgün ürün README'sinin M4 kabul durumunu güncel göstermemesidir; çalışan API'nin başarısız olduğu anlamına gelmez. B'nin bozuk veritabanında HTTP 200 döndüren sağlık kontrolü ise ayrıca doğrulanmış, ancak önceden belirlenmiş 48 senaryonun dışında tutulmuş bir kusurdur.

Veri bütünlüğü için A daha fazla SQLite kısıtı uygular. B ise daha az çalışma zamanı bağımlılığına sahiptir ve CSP, `nosniff`, çerçeveleme koruması gibi ek HTTP başlıklarını kullanır. Bu farklar bir ürünün bütün yönleriyle üstün olduğu sonucunu desteklemez. Ayrıntılar: [teknik karşılaştırma](minidesk/comparison.md) ve [48 testin tamamı](minidesk/results.md).

## Ölçülmeyenler ve karar

Gerçek tarayıcı/erişilebilirlik denetimleri ve hedef **Windows/Python 3.11** ortamındaki birincil koşu tamamlanamadı. API gecikmeleri, p95, CPU ve RAM ölçümlerinden geçerli karşılaştırmalı sonuç çıkmadı. 100 ve 1.000 kayıtlık eşdeğer sentetik verilerle SQLite dosya boyutları gözlendi; bunlar nihai hız veya kaynak puanı değildir.

**Sonuç:** İki ürünün temel işlevleri büyük ölçüde doğrulandı; A'nın veri korumalarında, B'nin bazı HTTP başlıklarında ve dağıtım sadeliğinde üstünlükleri var. Tarayıcı, performans ve hedef platform kanıtları eksik olduğundan **kazanan ilan edilmedi**. Ürün farklarının doğrudan AI Engineer kullanımından kaynaklandığı da ispatlanmadı.

## Gerçek uygulama kaynakları

İki MiniDesk yazılımının **çalıştırılabilir kaynak paketleri** yayımlanmıştır. Statik site Python kodunu çalıştırmaz; ZIP dosyalarını tarayıcıda açarak `.py`, `.js`, `.sql`, README ve test kaynaklarını görüntüler. Uygulamaları çalıştırmak için paketi indirip kendi bilgisayarınızda ilgili README yönergelerini kullanmanız gerekir.

| Ürün | Kaynak paketi |
|---|---|
| **A — AI Engineer kullanılan MiniDesk** | [with-ai-engineer.zip](minidesk/applications/with-ai-engineer.zip) |
| **B — Referans MiniDesk** | [without-ai-engineer.zip](minidesk/applications/without-ai-engineer.zip) |

İki arşivde de ürünün kök dizininde MIT `LICENSE` dosyası bulunur; telif bildirimi yayıncı adı olarak `PRAVECT` kullanır. Bu lisans yalnız MiniDesk örnek uygulamalarının lisanslama hakkı bulunan kaynaklarını kapsar; PRAVECT ürününün kendi kaynak kodlarına uygulanmaz. İndirilebilir arşivlerin güncel SHA-256 değerleri [yöntem belgesinde](minidesk/methodology.md) ve özgün kaynak paketlerinden farklarıyla birlikte verilmiştir. Lisans bildiriminin gerçek hak sahipliğiyle uyumu yayıncının sorumluluğundadır.

## Ayrıntılar ve kaynaklar

| Belge | Ne içerir? |
|---|---|
| [Yöntem](minidesk/methodology.md) | Üretim deneyi, sürümler, önceden belirlenen karşılaştırma, ölçüm ortamı |
| [Teknik karşılaştırma](minidesk/comparison.md) | Gerçek ürünlerin kod, mimari, veri ve güvenlik özellikleri |
| [Sonuçlar](minidesk/results.md) | 48 senaryonun tamamı, test kapsamı, performansın durumu ve dosya boyutları |
| [Sınırlamalar](minidesk/limitations.md) | Engeller, doğrulama boşlukları, sansürlenmiş kanıtların sınırları, neden atfetme |
| [Nihai ortak test kayıtları](minidesk/evidence/selected/COMMON_CASES.csv) | 48 senaryonun iki üründeki 96 nihai durumu; [önceden belirlenen test matrisi](minidesk/evidence/selected/TEST_CASES.csv) farklı, tarihsel bir kayıttır |

**Yayın ve gizlilik notu:** Bu dizin, geniş tarihsel arşivin seçilmiş bir sunumudur. İlk 1.800'den fazla yayımlanmış deney kaydı, iç kural bağlamları, özel imzalar ve ham günlükler bu sade sürümde yer almaz; asıl özel arşivden silinmiş oldukları anlamına gelmez. Seçilmiş kayıtlar özgün imzalı deney zincirinin tamamını bağımsız olarak doğrulamaya yetmez. Eski PRAVECT ürün kaynak kodu bu dizinin parçası değildir.
