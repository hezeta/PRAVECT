# PRAVECT

**Yapay zekâ kodlama ajanları için proje bağlamı, mühendislik disiplini ve doğrulama araçları.**

**Geliştirme ön gösterimi · Tarihsel teknik durum: 13 Ekim 2026**

> **Güncellik (16 Ekim 2026):** Bu belgeler 13 Ekim tarihli önceki ürün tabanını anlatır. PRAVECT için VS Code eklentisi merkezli yeni bir tasarım yönü belirlenmiştir; bu yapı henüz bu pakette uygulanmış veya doğrulanmış değildir.

**Başlangıç:** [PRAVECT ne sağlar?](FEATURES.md)
Proje hedeflerinden görev kapsamına ve sonuçların değerlendirilmesine uzanan kısa ürün özeti.

PRAVECT, yapay zekâ kodlama ajanlarının proje hedefleriyle tutarlı çalışmasını
destekleyen bir mühendislik araç setidir. Proje bağlamını yapılandırma, göreve uygun
mühendislik kurallarını hazırlama, kapsam ve doğrulama sözleşmeleri oluşturma,
değişiklikleri incelemeye bağlama ve yürütmeyi gözlemleme katmanlarını bir araya getirir.

Geliştirmenin amacı, doğruluk ve güvenlik sınırlarını korurken gereksiz bağlam yükünü,
tekrarları ve toplam iş akışı maliyetini azaltmaktır. Genel fayda, karşılaştırmalı ölçümlerle sonraki aşamada değerlendirilecek.

Bu yayın, önceki tabanın geliştirme belgelerini ve örnek verilerle çalışan etkileşimli arayüz gösterimini içerir. 13 Ekim itibarıyla çalışan çekirdek araçları ve VS Code prototipi bulunuyordu; indirilebilir PRAVECT sürümü, kurulum paketi veya açık alfa programı bulunmuyor. Korunan yürütme ve uçtan uca kabul, önceki tabanda tamamlanmamıştı.

## Hangi sorunu ele alıyor?

Bir kodlama ajanının doğru dosyayı düzenlemesi, görevin tamamlandığı anlamına gelmez.
Projenin amaçlarını doğru anlaması, ilgili kuralları kullanması, görev kapsamını
koruması ve ürettiği değişikliği uygun biçimde doğrulaması da gerekir.

PRAVECT bu işlerin daha açık, tekrar kullanılabilir ve incelenebilir bir süreç içinde
yürütülmesini destekler. Aynı zamanda bu sürecin kendi maliyetini de sorgular:
gereksiz kontrol, tekrar okuma ve kullanıcı müdahalesi de azaltılması gereken yüktür.

## 13 Ekim tabanında bulunan katmanlar

| Katman | Ne sağlar? |
|---|---|
| Proje bağlamı | ROADMAP'tan yapılandırılmış proje profili; depo bulguları ile hedeflerin ayrılması |
| Mühendislik bağlamı | Seçilmiş politika paketlerinden ilgili kuralların derlenmesi |
| Görev sözleşmesi | Kapsam, doğrulama gereksinimleri, durma koşulları ve yetki bilgilerinin yapılandırılması |
| Değişiklik ve inceleme | Dosya/revizyon bağları, aday dondurma ve inceleme girdilerinin tutarlılık kontrolleri |
| Kurulum yaşam döngüsü | Yönetilen dosya bütünlüğü, yükseltme, geri alma ve kesinti sonrası kurtarma araçları |
| IDE ve gözlem | VS Code paneli, Python köprüsü, ayrı Codex oturumu ve sınırlı yürütme ölçümleri |

Bu tarihsel katmanların kapsamı [13 Ekim özellik durumunda](status/FEATURE_STATUS.md) açıklanır.

## Bir iş akışında nasıl kullanılır?

1. Projenin hedefleri ve depoda gözlenen durum ayrıştırılır.
2. Görev için kapsam, değişiklik sınıfı ve gerekli mühendislik bağlamı hazırlanır.
3. Ajanın çalışması görev sözleşmesi çerçevesinde yürütülür.
4. Değişiklik, doğrulama ve inceleme girdileri aynı adayla ilişkilendirilir.
5. Sonuç, eldeki kanıt ve açık kalan sınırlarla değerlendirilir.

Bu, çekirdeğin desteklediği çalışma modelidir. Girdilerin bir bölümü ajan veya geliştirici tarafından hazırlanır; araçlar bunları işler ve denetler. Ayrıntılar:
[mimari ve işleyiş](docs/ARCHITECTURE.md), [görev sözleşmesi](docs/TASK_CONTRACT.md).

## 13 Ekim itibarıyla geliştirme durumu

O tarihteki geliştirme VS Code ve Codex üzerinde yoğunlaşıyordu. Gerçek IDE ortamındaki
sınırlı bir gözlem kalibrasyonu, 16 çalıştırma ve sekiz OFF/ON çiftinin tamamlanmasıyla
sonuçlandı. Bu, ölçüm yolunun gerçek ortamda doğrulandığı sınırlı bir çalışmadır. [Ölçüm özeti](evidence/CALIBRATION_SUMMARY.md).

O tarihte yürütme ortamı, doğrulayıcı ve kanıt üreticisi arasındaki koruma sınırı açık
bir çalışma konusuydu. Bu durum [tarihsel yol haritasında](status/ROADMAP.md) ve [bilinen sınırlarda](status/LIMITATIONS.md) kayıtlıdır.

## Daha fazla bilgi

Mevcut eklenti tamamlandıktan sonraki hedeflerden biri, teknik gerçekliği, proje
niyetini ve gözlenebilir ajan faaliyetlerini graph/vector tabanlı zamansal bir
mühendislik belleğinde ilişkilendirmektir. **Bu genişletme henüz uygulanmadı.**
[İleriye dönük mühendislik belleği hedefi](docs/ENGINEERING_MEMORY.md).

- [Ürün amacı ve kullanım yaklaşımı](docs/OVERVIEW.md)
- [Araştırmanın soruları ve ürünle ilişkisi](docs/RESEARCH.md)
- [Kanıtların nasıl yorumlandığı](docs/EVIDENCE_MODEL.md)
- [Seçilmiş doğrulama özetleri](evidence/README.md)
- [MiniDesk deneyi ve karşılaştırması](tests/README.md)
- [Geliştirme günlüğü](devlog/README.md)
- [Geliştirme değişiklikleri](CHANGELOG.md)

PRAVECT bu ön gösterimin adıdır. Mevcut teknik kaynaklar ve tarihsel kayıtlar
**AI Engineer Kit** adını taşır; bu durum kaynak kodunun yeniden adlandırıldığını
veya yeni bir sürümün yayımlandığını duyurmaz. Kaynak tabanı 2.1.1-rc.1, geliştirme
hedefi 2.2'dir. Kaynak kodu ve lisans yayını bu ön gösterimden ayrı kararlardır.

**Resmî web sitesi:** [pravect.com](https://pravect.com/)

PRAVECT'in tanıtımını, geliştirme durumunu, teknik belgelerini ve MiniDesk deney sonuçlarını web sitesinden inceleyebilirsiniz.

Bu çalışma bağımsız bir projedir; adı geçen IDE veya model sağlayıcılarının resmî
ürünü ya da onayladığı bir entegrasyon olarak sunulmaz.