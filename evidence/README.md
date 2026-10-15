# Seçilmiş doğrulama özetleri

[Ana sayfa](../README.md) · Derleme tarihi: 13 Ekim 2026

Bu dizin, geliştirme arşivindeki kayıtların yayıma yönelik seçilmiş özetlerini içerir.
Yeni bir test çalıştırmasının çıktısı veya bağımsız sertifikasyon değildir. Ham
artefaktlar ve tam yeniden üretim paketi bu belgelerle birlikte sunulmamaktadır.

| Kayıt | Hangi soruyu cevaplar? | Temel sınır |
|---|---|---|
| [Araştırma değerlendirmesi](RESEARCH_SUMMARY.md) | Belirlenen yaklaşımlar literatürden ne ölçüde destek alıyor? | Ürün etkinliğini ölçmez |
| [IDE kalibrasyonu](CALIBRATION_SUMMARY.md) | Tanımlı OFF/ON gözlem akışı ve tüm örneklerin raporlanması tamamlandı mı? | Genel ürün faydasını veya tüm IDE maliyetini ölçmez |
| [HOST erişim gözlemi](HOST_SUMMARY.md) | Belirli gerçek worker/parent örneklerinde hangi erişimler gözlendi? | Korunan HOST mimarisinin tamamlandığını göstermez |

## Her özetin başlık bloğu

Her kayıt aynı yedi alanla başlar: **Durum**, **Tarih**, **Ortam / sürüm**, **Kanıt düzeyi**,
**Kanıtlar**, **Kanıtlamaz** ve **Kısaca**. Böylece bir sonucun neyi gösterdiği ve neyi
göstermediği ayrıntıya girmeden okunabilir. Etiketlerin anlamı
[kanıt modelinde](../docs/EVIDENCE_MODEL.md) açıklanır.

## Özetlerde korunan bilgiler

Her kayıt tarih, konu/ortam, yöntem, beklenen ve gözlenen sonuç ile yorum sınırını
belirtir. Başarısız veya tamamlanmamış alanlar gizlenmez. Yerel kullanıcı yolları,
konuşma kimlikleri, token/parola ve ham model metinleri yayımlanmaz.

Kayıtların dayanağı, özel arşivdeki isimleriyle tanımlanmıştır. Bu adlar kamuya açık
bağlantı değildir; okuyucunun elinde olmayan dosyaya kırık bağlantı verilmez. İleride
tam artefakt yayımlanırsa kimlikten arındırılmış, kapsamı ve yeniden üretim koşulları
açıklanmış ayrı bir teslim olmalıdır.

[Durum etiketlerinin anlamı](../docs/EVIDENCE_MODEL.md)
