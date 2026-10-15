# MiniDesk — Sınırlamalar ve kanıt güvenilirliği

[Genel özet](../README.md) · [Yöntem](methodology.md) · [Sonuçlar](results.md)

## Deneyin neyi kanıtlamadığı

Bu yayın iki MiniDesk ürününün ve önceki AI Engineer kitiyle yürütülen belirli bir üretim deneyinin özetidir. Güncel PRAVECT eklentisinin çalışan kaynaklarını, genel güvenilirliğini veya yeni mimarisini doğrulamaz. Başlangıç kiti 2.1.1-rc.1 temel alınmış ve deney sırasında düzeltmeler uygulanmıştır; sonuç saf, değiştirilmemiş ilk sürüme atfedilemez.

Her yöntem için yalnız birer gerçek ürün bulunduğundan sonuçlar istatistiksel olarak genel başarı oranı veya **nedensel etki** göstermez. Flask ile `http.server` farkı, değişik dağıtım koşulları, test stratejileri ve insan katılımı birlikte etkilidir. Kayıtlı 311 komut, model token maliyeti ya da etkin insan çalışma süresi olarak kullanılamaz. Önceki raporlarda bu değerler **UNKNOWN** durumundadır. Codex/Windows izin ve oturum sorunları kanıt olmadan AI Engineer'a mal edilemez.

## Karşılaştırmanın eksik ölçümleri

- Hedef **Windows/Python 3.11** birincil sınaması ve temiz kurulum denemeleri tamamlanmadı.
- Gerçek Chromium/Edge gezinmesi, klavye kullanımı, mobil düzen ve erişilebilirlik ölçümleri bu çalışma ortamında engellendi (`BLOCKED`). Bu yüzden tam tarayıcı kalitesi için PASS/FAIL yoktur.
- API p50/p95, CPU, RAM, soğuk başlatma ve hata oranı için tamamlanmış tarafsız ölçüm yoktur. Başlatılan Linux performans denemeleri zaman sınırında kesildi; kısmi veriler hız üstünlüğüne çevrilmedi.
- D07 (tam şema kuralları), S04 (tam hassas veri taraması), U05 (form erişilebilirliği) ve Q03 (bütünsel kod yapısı) gerçek kapsamı karşılamadığı için `NOT_ASSESSED` olarak yeniden sınıflandırılmıştır.
- S07 (kimlik doğrulama), ROADMAP'in yerel ve tek kullanıcılı ürün sınırı nedeniyle `NOT_APPLICABLE` durumundadır. Bu, internete açık dağıtım için güvenlik onayı değildir.
- Ürünlerin kendi 59 ve 38 testleri doğrudan eşdeğer test takımı değildir. Python ifade kapsamı JavaScript'i, dalları ve gerçek tarayıcıyı kapsamıyor.
- 100 ve 1.000 kayıt için SQLite dosya boyutu farkları tekil ikincil gözlemlerdir; hız veya genel kalite üstünlüğü değildir.

## Seçilmiş kamu kanıtlarının kapsamı

Sade deney belgelendirmesinde **11 belge/kanıt dosyası** vardır: ana README, dört tamamlayıcı belge ve altı seçilmiş kanıt kaydı. Bunlara ek olarak iki MiniDesk uygulamasının kaynakları **iki ayrı ZIP arşivi** olarak [uygulamalar bölümünden](../README.md) indirilebilir. Tam çalışma günlükleri, kanıt indeksleri, derlenmiş iç politika/kural bağlamları ve imzalı operatör kayıtları bu kamu sunumuna alınmadı. **Yayımlanmamaları özel arşivden silindikleri anlamına gelmez.** Bu sürüm geçmiş bütün işlemleri yeniden oluşturacak bir arşiv değildir.

Önceki geniş kamu deney paketinde özgün 2.169 girdinin 356'sı yalnız metaveriyle temsil edilmişti; yaklaşık 95.641 oturum başvurusu sansürleme sonucunda birbirinden ayırt edilemez duruma gelmişti. Özgün imzalı belgelerin sansürlenmiş kopyaları geçerli kriptografik imza sağlamıyordu. Bu yeni pakette o ayrıntılı kopyalar da bulunmadığından **kamuya açık dosyalar tek başına M0–M4 kabul zincirini bağımsız olarak doğrulayamaz.** Kabul bilgileri tarihsel raporlardan aktarılmış, yeni bir kabul denetimi yapılmamıştır.

Seçilmiş altı kanıt dosyası, önceki yayın paketindeki karşılıklarının **değiştirilmemiş bayt kopyalarıdır**. Ürün kodları ve testleri de değiştirilmedi; ancak yayımlanan iki ZIP'in MIT telif bildirimi tamamlandı ve B'deki eksik ROADMAP dosyası özgün kaynaktan geri kondu. Bu yüzden yayımlanan ZIP'ler tarihsel ZIP'lerle aynı hash'i taşımaz. [Yöntem belgesinde](methodology.md) özgün kaynak ve dağıtım ZIP'lerinin ayrı SHA-256 değerleri açıklanır. SHA-256 yalnızca dosya bütünlüğünü karşılaştırmaya yarar, deneyin bütün kabul zincirini doğrulamaz.

Kamu kaydında bırakılan veriler deney sonuçlarını açıklamak içindir. PRAVECT'in kapalı kaynaklı, ticari olarak korunacak iç kural tanımları bu dosyalarda yayımlanmaz. Bu seçimin bütün fikrî mülkiyet risklerini ortadan kaldırdığı iddia edilmez.

## Yayın ve yeniden kullanım sınırı

Bu, **eski deneyin sadeleştirilmiş sunumudur**; uygulama kodunu veya sonuçları değiştirmez, yeni test başlatmaz ve PRAVECT'in yeni sürümünü yayımlamaz. Yalnız kamu uygulama arşivlerinin lisans ve dosya bütünlüğü düzeltmeleri yapılmıştır. Önceki geniş paketin kaldırılan kayıtlarına artık kamu bağlantısı verilmez. Eski `tests/` ağacının üzerine dosya eklemek yerine, eski ağacı bütün olarak yeni `tests/` diziniyle değiştirmek gerekir; aksi hâlde eski kayıtlar yayımlanmaya devam eder.

Açık durum: **KISMİ KARŞILAŞTIRMA — nihai puan veya kazanan yok.**
