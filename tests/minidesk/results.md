# MiniDesk — Bütün test ve ölçüm sonuçları

[Genel özet](../README.md) · [Yöntem](methodology.md) · [Teknik karşılaştırma](comparison.md) · [Sınırlamalar](limitations.md)

Bu sayfa 15 Ekim 2026 tarihli **Linux/Python 3.13.5 ikincil** sınamasından aktarılmış sonuçları içerir. Ürünler veya testler bu sadeleştirme sırasında yeniden çalıştırılmadı. A, AI Engineer kullanılan; B, referans üründür.

## Genel tablo

| Gösterge | A | B |
|---|---:|---:|
| Ürünün kendi otomatik testleri | 59/59 PASS | 38/38 PASS |
| Ortak senaryo sayısı | 48 | 48 |
| PASS | 31 | 32 |
| FAIL | 1 | 0 |
| BLOCKED | 11 | 11 |
| NOT_ASSESSED | 4 | 4 |
| NOT_APPLICABLE | 1 | 1 |
| Python ifade kapsamı | %98,57 — 276/280 | %93,37 — 310/332 |

Dört `NOT_ASSESSED` senaryosu iki ürün için de D07, S04, U05 ve Q03'tür. S07 ise ROADMAP gereği kapsam dışındadır. **A'nın tek FAIL sonucu O05 (eski README kabul durumu)**; bütün diğer ortak işlev testleri başarılıdır. Kaynak CSV: [96 sonuç satırı](evidence/selected/COMMON_CASES.csv).

## Önceden belirlenen 48 ortak senaryo

Bu tablodaki başlıklar [özgün 48 senaryonun](evidence/selected/TEST_CASES.csv) kullanıcı odaklı kısa tanımlarıdır; sonuçlar son ortak kayıt CSV'sinden alınmıştır.

| Kod | Senaryo | A | B |
|---|---|---|---|
| `F01` | Talep oluşturma, kimlik ve zaman alanları | PASS | PASS |
| `F02` | Başlık uzunluğu ve Unicode sınırları | PASS | PASS |
| `F03` | Açıklama sınırı, varsayılan öncelik | PASS | PASS |
| `F04` | Öncelik ve tarih doğrulama | PASS | PASS |
| `F05` | Düzenlenebilir alanların sınırları | PASS | PASS |
| `F06` | Geçerli durum geçişleri | PASS | PASS |
| `F07` | Yasak durum geçişlerinin reddi | PASS | PASS |
| `F08` | Türkçe metin arama | PASS | PASS |
| `F09` | Birleşik filtreler ve sıralama | PASS | PASS |
| `F10` | Özet sayaçları ve gecikme durumu | PASS | PASS |
| `F11` | Geçmiş ve olay kayıtları | PASS | PASS |
| `F12` | JSON dışa aktarma | PASS | PASS |
| `F13` | Yeniden başlatma sonrası kalıcılık | PASS | PASS |
| `F14` | HTTP hata yanıtları | PASS | PASS |
| `F15` | Zorunlu API uç noktaları | PASS | PASS |
| `F16` | Ağ kesintisinin arayüzde bildirilmesi | BLOCKED | BLOCKED |
| `D01` | SQLite şeması ve ilişkiler | PASS | PASS |
| `D02` | Oluşturma hatasında geri alma | PASS | PASS |
| `D03` | Düzenleme hatasında geri alma | PASS | PASS |
| `D04` | Durum geçişinde atomik kayıt | PASS | PASS |
| `D05` | Değişmez alanların korunması | PASS | PASS |
| `D06` | Sentetik veri yalıtımı | PASS | PASS |
| `D07` | Şema kısıtlarının kapsamlı zorlanması | NOT_ASSESSED | NOT_ASSESSED |
| `D08` | SQLite bütünlük denetimi | PASS | PASS |
| `S01` | Gerçek DOM üzerinde HTML/JS enjeksiyonu | BLOCKED | BLOCKED |
| `S02` | SQL enjeksiyonuna direnç | PASS | PASS |
| `S03` | Yerel ağ adresine bağlanma sınırı | PASS | PASS |
| `S04` | Bütün dosyalarda hassas veri denetimi | NOT_ASSESSED | NOT_ASSESSED |
| `S05` | Bilinmeyen isteklerin reddi | PASS | PASS |
| `S06` | Tarayıcıda güvenli metin gösterimi | BLOCKED | BLOCKED |
| `S07` | Kimlik doğrulamanın kapsamı | NOT_APPLICABLE | NOT_APPLICABLE |
| `S08` | HTTP güvenlik başlıklarının gözlemi | PASS | PASS |
| `S09` | Büyük JSON isteği ve hata yönetimi | PASS | PASS |
| `U01` | Türkçe arayüz iş akışları | BLOCKED | BLOCKED |
| `U02` | Mobil ve masaüstü ekran taşması | BLOCKED | BLOCKED |
| `U03` | Klavyeyle kullanım | BLOCKED | BLOCKED |
| `U04` | Boş, yüklenme ve hata durumları | BLOCKED | BLOCKED |
| `U05` | Form etiketleri ve erişilebilirlik ilişkileri | NOT_ASSESSED | NOT_ASSESSED |
| `U06` | Kullanıcı girdisinin tarayıcıda gösterimi | BLOCKED | BLOCKED |
| `O01` | Windows temiz kurulum | BLOCKED | BLOCKED |
| `O02` | Windows çevrimdışı test koşusu | BLOCKED | BLOCKED |
| `O03` | Dış ağa çıkmadan API kullanımı | PASS | PASS |
| `O04` | README çalıştırma yönergeleri | PASS | PASS |
| `O05` | README ve son kabul durumu tutarlılığı | FAIL | PASS |
| `Q01` | Yasak teknoloji/bağımlılık denetimi | PASS | PASS |
| `Q02` | Test kapsamının kaynak düzeyinde incelenmesi | PASS | PASS |
| `Q03` | Bütünsel kod kalitesi ve yapı incelemesi | NOT_ASSESSED | NOT_ASSESSED |
| `Q04` | Görsel kullanılabilirlik ve geri bildirim | BLOCKED | BLOCKED |

**Sonuç sınıflandırması önemlidir:** `BLOCKED` ürün hatası değildir. `NOT_ASSESSED` başarı değildir. S08'deki PASS, başlık varlığına ilişkin puansız gözlem yapıldığı anlamına gelir. O04 yalnız README yönergelerinin kaynak düzeyinde bulunduğunu gösterir; temiz Windows kurulumu değildir. Q03, D07, S04 ve U05 dosya/etiket varlığından daha derin denetim gerektirdiği için PASS sayılmadı.

## Performans ve kaynak kullanımı

| Kod | Ölçüm | Durum | Gerekçe |
|---|---|---|---|
| P01 | Soğuk başlatma | NOT_ASSESSED | Nihai karşılaştırmalı veri yok |
| P02–P05 | Listeleme, arama, detay, özet/dışa aktarma gecikmeleri | BLOCKED | Hedef Windows ortamı yok; ikincil ölçümler zaman sınırında kesildi |
| P06 | Yazma işlemlerinin gecikmesi | NOT_ASSESSED | Tamamlanmış koşu yok |
| P07 | İstek hata oranı | NOT_ASSESSED | Eşlenmiş koşu tamamlanmadı |
| R01–R02 | RAM ve CPU | NOT_ASSESSED | Geçerli karşılaştırmalı örneklem yok |
| R03 | SQLite dosya boyutu | SECONDARY_OBSERVATION | Eşdeğer sentetik veriyle tekil gözlem |
| R04 | Paket/bağımlılık bilgisi | OBSERVED | Kaynak arşivleri ve bağımlılıklar incelendi |
| R05 | Windows temiz kurulum | BLOCKED | Birincil platform bu ortamda yok |

### Gözlemlenen SQLite boyutları

| Sentetik veri | A | B |
|---|---:|---:|
| 100 kayıt, 185 olay | 102.400 bayt | 86.016 bayt |
| 1.000 kayıt, 1.850 olay | 856.064 bayt | 724.992 bayt |

Bu gözlem yalnız depolama alanına ilişkindir; işlem süresi, RAM veya genel yazılım verimliliği puanı değildir. Mantıksal veri kümelerinin eşleşen parmak izleri [veri denetim dosyasında](evidence/selected/FIXTURE_CHECKS.json) bulunmaktadır.

## Ön kayıt dışında ek tanılama

Sentetik veritabanındaki tablolar kaldırıldığında `/api/health`, A'da **HTTP 503**, B'de **HTTP 200** döndürdü. B'nin sağlık bildirimi bu hata koşulunda yanıltıcıydı. Ayrıntı: [ek tanılama](evidence/selected/EXTRA_DIAGNOSTICS.json). Bu bulgu 48 senaryonun puanına sonradan eklenmedi.

## Nihai değerlendirme durumu

**KISMİ.** Birincil Windows/Python 3.11 koşusu, gerçek tarayıcı, p50/p95, bellek, CPU ve bazı tam kapsamlı kod/güvenlik denetimleri eksik. 100 puanlık nihai sonuç ve kazanan hesaplanmadı. Python ifade kapsamının [özgün ölçüm kaydı](evidence/selected/COVERAGE_METRICS.json) yalnız Python testlerini kapsar; JavaScript ve tarayıcıyı kapsamaz.
