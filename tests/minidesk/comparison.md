# MiniDesk — İki gerçek ürünün teknik karşılaştırması

[Genel özet](../README.md) · [Yöntem](methodology.md) · [Test tabloları](results.md) · [Sınırlamalar](limitations.md)

Karşılaştırma iki gerçek ürünün gözlemlenen farklarını değerlendirir: **A — AI Engineer kullanılan üretim**, **B — referans üretim**. Tek birer ürünün farklı geliştirme süreçlerinden çıkması, farkların nedeninin mutlaka AI Engineer olduğunu kanıtlamaz. İki ürün ortak [ROADMAP'e](evidence/selected/ROADMAP.md) dayanır; Flask tercih edilmiş bir teknoloji olup zorunlu değildi.

## Kod ve yapı

| Ölçüt | A | B |
|---|---|---|
| HTTP katmanı | Flask 3.1.3 | Python standart `http.server` |
| Veri katmanı | SQLite | SQLite |
| İş kuralları | `items.py` | `service.py` |
| Doğrulama | `validation.py` | `validation.py` |
| Python uygulama kodu | 488 satır | 466 satır |
| Haricî çalışma zamanı bağımlılığı | Flask ve bağımlılıkları | Yok |
| Makinece okunabilir API sözleşmesi | OpenAPI var | Ayrı OpenAPI yok |

A HTTP yönlendirmesini yerleşik bir çatıya bırakır; fakat `items.py` modülünde iş kuralları ve SQL erişimi iç içedir. B'de hizmet/veritabanı sorumluluk ayrımı daha belirgindir; buna karşılık doğrudan HTTP işleme sorumluluğu uygulamada kalır. Daha az satır veya bağımlılık tek başına daha iyi tasarım anlamına gelmez. Bütünsel değiştirilebilirlik incelemesi ortak Q03 senaryosunda **NOT_ASSESSED** durumundadır.

## Doğruluk ve veri koruması

Her iki ürün de talep oluşturma, düzenleme, durum geçişleri, geçmiş, filtreler ve JSON dışa aktarmanın temel dış senaryolarını geçti. Hata durumlarında atomik yazım ve geri alma testleri de geçti. A'nın SQL şeması başlık/açıklama uzunlukları ve olay JSON geçerliliği gibi kurallarda daha fazla veritabanı düzeyi kısıt taşır. B daha çok uygulama katmanında doğrulamaya dayanır. Bu, A lehine somut koruma farkıdır; tek başına bütün güvenlik veya performans üstünlüğü değildir.

Ek tanılamada sentetik veritabanındaki tablolar kaldırılınca A'nın `/api/health` yanıtı **503**, B'ninki **200** oldu. B'nin sağlık denetimi bu koşulda gerçekte kullanılmaz hâle gelen veri katmanını doğru bildirmiyordu. Bu sonuç **48 önceden belirlenen senaryo dışında** gözlemlendi; puana sonradan katılmadı. [Ek tanılama kaydı](evidence/selected/EXTRA_DIAGNOSTICS.json).

## Güvenlik ve çalışma sınırları

İki üründe parametreli SQL sorguları ve sunucu tarafında girdi doğrulama bulunuyor. A ve B yalnız yerel `127.0.0.1` kullanımını hedefliyor. B'nin HTTP yanıtlarında CSP, `X-Content-Type-Options: nosniff` ve `X-Frame-Options: DENY` mevcut; A'da aynı başlıklar gözlenmedi. B ayrıca 128 KiB açık istek gövdesi sınırı tanımlıyor; A'da eşdeğer açık uygulama sınırı tespit edilmedi. A ise arama girdisinin uzunluğunu sınırlandırıyor. Bunlar yerel kullanım bağlamında değerlendirilmesi gereken savunma farklarıdır, bağımsız istismar ispatı değildir.

Kimlik doğrulama ve internete yayın ROADMAP kapsamı dışında. Tarayıcıda DOM tabanlı HTML/JavaScript enjeksiyonu, klavye kullanımı ve arayüz güvenliği gerçek tarayıcıyla bu karşılaştırmada sınanamadı. **S08 PASS**, yalnız HTTP başlıklarının incelendiğini belirtir; korumaların aynı olduğu anlamına gelmez.

## Testler, belgeler ve taşıma

A'nın kendi testi **59/59**, B'ninki **38/38** başarılı. Python ifade kapsamı A'da **%98,57**, B'de **%93,37**; bu oranlar JavaScript, dal kapsamı veya tarayıcı etkileşimini içermez. A ürün README'si M4 kabul durumunu güncel göstermediğinden O05 testinde **FAIL** aldı. B aynı belgede **PASS** aldı. Başarısızlık ürünün API işleviyle ilgili değildir.

A'nın Windows/Python 3.11 için hazırlanan çevrimdışı bağımlılıkları hedef platforma bağlıdır. B haricî çalışma zamanı paketi gerektirmez; bu, taşıma sadeliği sağlar. Buna karşılık iki ürünün Windows temiz kurulumları karşılaştırmalı olarak test edilmedi.

## Performans ve genel sonuç

Güvenilir p50/p95 HTTP gecikmesi, CPU ve RAM karşılaştırması yoktur. Sentetik veriyle gözlenen SQLite boyutları [sonuçlarda](results.md) yer alır; B daha az disk alanı kullanmıştır, fakat tek bir gözlemden genel performans üstünlüğü çıkarılamaz.

**Bulgular katmana bağlı:** A veri şeması ve test kapsamı bakımından, B HTTP başlıkları ve bağımlılık sadeliği bakımından güçlü. Eksik ölçümler ve gerçek tarayıcı kontrolleri nedeniyle genel puan ya da kazanan belirtilmez.
