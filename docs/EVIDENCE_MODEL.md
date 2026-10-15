# Kanıt modeli ve durumların anlamı

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

Bir iddianın dayanağı, bir kontrolün sonucu ve bir özelliğin geliştirme durumu ayrı
bilgilerdir. Tek bir "doğrulandı" etiketi altında birleştirilmez.

## Bilginin dayanağı

| Etiket | Anlamı |
|---|---|
| VERIFIED | Belirtilen dar iddia doğrudan kanıtla destekleniyor. Örneğin bir dosyanın varlığı. |
| INFERRED | Eldeki veriden çıkarım yapılmış; doğrudan gözlemden ayrı tutuluyor. |
| UNKNOWN | Yeterli bilgi yok veya gerekli görünürlük sağlanmamış. |

Bir bağımlılığın dosyada tanımlı olması, aktif çalışma zamanında kullanıldığını
kanıtlamayabilir. VERIFIED etiketi hangi iddiaya aitse yalnız onu kapsar.

## Kontrol sonucu

| Etiket | Anlamı |
|---|---|
| PASS / FAIL | Belirli kontrolün tanımlı ölçütü karşılaması / karşılamaması |
| OBSERVED | Gözlem elde edilmiş olması; güvenlik veya görev doğruluğu kabulü değildir |
| NOT_ASSESSED | Bu sonuç kapsamında değerlendirilmemiş alan |
| UNSUPPORTED / BLOCKED | Gereken yeteneğin desteklenmemesi veya önkoşul eksikliği nedeniyle ilerlenememesi |

Etiketler araç sözleşmeleriyle birlikte okunur. Üst düzey bir PASS, rapordaki
NOT_ASSESSED alanlarını tamamlanmış yapmaz.

## Geliştirme durumu

Tasarlanmış, kaynakta uygulanmış, yerel test edilmiş, gerçek ortamda gözlenmiş ve
kullanıcı faydası karşılaştırmalı ölçülmüş durumları farklıdır. [Özellik tablosu](../status/FEATURE_STATUS.md)
bu ayrımı izler; bütün ürün için tek bir tamamlanma yüzdesi vermez.

## Kanıt zinciri

Bir sonuç açıklanırken görev, aday sürümü/içeriği, ortam, yöntem, beklenen sonuç,
gözlenen sonuç ve yorum sınırı birlikte belirtilmelidir. Hash içerik bağını sağlar;
üreticinin yetkili veya iddiasının doğru olduğunu tek başına kanıtlamaz.

Benzer biçimde testlerin geçmesi oracle'ın tüm hataları yakaladığını; ayrı model
kullanılması da değerlendirmelerin hatalarının bağımsız olduğunu göstermez.

## Yayımlanan kanıtların düzeyi

Buradaki evidence belgeleri, özel geliştirme arşivindeki kayıtların seçilmiş Türkçe
özetleridir. Ham loglar, tam kaynak adayı ve yeniden çalıştırma ortamı bu sitede
yer almaz. Okuyucu özetlerden bütün sonuçları bağımsız olarak yeniden üretemez.

Kişisel yollar, süreç ve sohbet kimlikleri gibi ayrıntılar yayıma yönelik özetlere
taşınmaz. Bu çıkarma işlemi sonuçları değiştirmek veya başarısız denemeleri gizlemek
için kullanılmaz; özetlerin kapsamı ve eksikleri açıkça belirtilir.

[Kanıt dizini](../evidence/README.md) · [bilinen sınırlar](../status/LIMITATIONS.md)
