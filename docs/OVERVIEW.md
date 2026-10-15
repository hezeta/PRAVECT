# Ürün amacı ve kullanım yaklaşımı

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

## Temel amaç

PRAVECT, yapay zekâ destekli yazılım geliştirmede doğru sonuca ulaşmak için gereken
mühendislik bağlamını ve kontrolleri daha düzenli kullanmayı hedefler. Verimlilik;
yalnızca daha az token tüketimi değil, gereksiz araç çağrılarının, tekrarların,
onarım işlerinin ve insan müdahalesinin azalmasıyla birlikte değerlendirilir.

## Kimin için geliştiriliyor?

Proje üzerinde AI kodlama ajanlarıyla çalışan ve görev kapsamını, proje kararlarını,
doğrulamayı ve sonuçların izlenebilirliğini birlikte yönetmek isteyen geliştiriciler
için geliştiriliyor. İlk bütünleşik arayüz VS Code üzerinde çalışıyor; mevcut native
yürütme çalışmaları Codex'e odaklanıyor.

Farklı ajan ortamları için adaptörler mevcut; yetenekleri aynı değil ve bugün doğrulanmış ortam Windows + Codex.

## Somut örnek

Örnek senaryo, küçük bir Python hatasının düzeltilmesidir.
PRAVECT'in desteklediği mühendislik yaklaşımında:

- Görevin amacı ile depoda gerçekten görülen durum ayrılır.
- Düzenlenebilecek dosyalar ve kapsam dışı alanlar tanımlanır.
- Değişiklik türüne uygun kurallar ve doğrulama gereksinimleri hazırlanır.
- İncelenecek değişiklik, dosya içerikleri ve görev sözleşmesiyle bağlanır.
- Sonuçlar aynı aday üzerinden değerlendirilir; eksik kanıt açık bırakılır.

Bu, ürünün işleyişini anlatan bir kullanım örneğidir.

## Mevcut çekirdek ve geliştirme hedefi

ROADMAP derleme, depo keşfi, politika bağlamı derleme, görev sözleşmesi, aday bağlama,
inceleme ve kurulum araçları kaynakta mevcuttur. VS Code eklentisi, bu yapıya arayüz
ve seçilmiş çalışma zamanı bağlantıları sağlar.

Devam eden çalışma, bu bileşenleri kullanılabilir bir iş akışında birleştirmek ve
görev kodundan korunmuş doğrulama/kanıt üretme sınırını tamamlamaktır. Sonraki
değerlendirmeler, mekanizmaların doğru sonuç ve toplam iş maliyetine katkısını ölçmelidir.

## Nasıl değerlendirilmelidir?

Bir özellik üç ayrı soruyla değerlendirilir: Kaynakta uygulanmış mı? Hangi ortamda ve
kapsamda doğrulanmış? Sağladığı fayda ölçülmüş mü? Bir sorunun olumlu
yanıtı diğerlerini otomatik olarak olumlu yapmaz.

İlgili belgeler: [özellik durumu](../status/FEATURE_STATUS.md),
[araştırma](RESEARCH.md), [kanıt modeli](EVIDENCE_MODEL.md).
