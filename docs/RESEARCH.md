# Araştırmanın amacı ve ürünle ilişkisi

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

## Araştırma sorusu

Temel soru, AI kodlama ajanlarının doğru işi daha az gereksiz işlem ve kullanıcı
yüküyle nasıl tamamlayabileceğidir. Doğruluk, güvenlik ve kanıt bütünlüğünden ödün
vermeden toplam iş akışı maliyetini azaltmak araştırmanın amacıdır.

Araştırma, mevcut mühendislik çekirdeğini değerlendirmek ve geliştirmek için kullanılır.
Daha fazla kural veya kontrol eklemek kendiliğinden ilerleme sayılmaz. Bir mekanizmanın
katkısı ile getirdiği gecikme, bağlam yükü ve bakım maliyeti birlikte incelenir.

## Araştırma eksenleri

| Eksen | Temel sorular |
|---|---|
| Deterministik araçlar ve durum | Hangi işler güvenilir araçlarla yapılmalı? Durum, revizyon ve kesinti sonrası süreklilik nasıl korunmalı? |
| Depo ve bağlam | Görev için hangi dosya, sembol ve kurallar gerekli? Daha fazla bilgi ne zaman işe yarıyor? |
| Yetenek ve yönlendirme | Göreve uygun araç/host seçimi nasıl yapılmalı? Fallback hangi yetenekleri kaybettirebilir? |
| Üretim ve doğrulama | Yanlış kabul ve yanlış ret nasıl ölçülmeli? Aynı hata kaynaklarını paylaşan değerlendiriciler nasıl ayırt edilmeli? |
| Toplam iş ekonomisi | Retry, onarım, inceleme, kullanıcı emeği ve başarısız denemeler dahil fayda nasıl ölçülmeli? |
| Güven ve yetki | Bağlamın kaynağı, işlem yetkisi ve sonuç üreticisinin kimliği nasıl ayrılmalı? |

Kod grafikleri, delta bağlamı, önbellek, bilgi edinme bütçeleri ve uyarlamalı durdurma
bu sorular altında araştırılmış yaklaşımlardır. Araştırmada yer almaları, üründe
uygulandıkları veya yol haritasına kesin özellik olarak alındıkları anlamına gelmez.

13 Ekim 2026'da graph/vector tabanlı zamansal mühendislik belleği, mevcut eklenti tamamlandıktan sonraki genişletme hedefi olarak ayrıca belirlendi. Bu,
araştırma bulgusundan otomatik türetilmiş bir gereklilik değil, ayrı ürün yönüdür.
Teknoloji seçimi ve uygulama başlamamıştır. [Hedefin kapsamı](ENGINEERING_MEMORY.md).

## Araştırmadan geliştirmeye geçiş

```text
İddia ve mevcut yaklaşım
  → kaynaklar ve karşı örnekler
  → hangi koşullarda uygulanabilir?
  → mevcut kodda karşılığı ve eksikliği
  → sınırlı değişiklik ve doğrulama
  → gerçek iş akışında fayda/maliyet değerlendirmesi
```

Araştırma arşivi; ilk raporları, sonraki düzeltmeleri, kaynak incelemelerini ve tarihli
deney sonuçlarını ayrı tutar. Eski bir öneri, yeni bir uygulamanın güncel durumunu
tek başına belirlemez. Başarısız deneyler olumlu sonuçlarla değiştirilmez.

## Literatür değerlendirmesinin sonucu

5 Ekim 2026 tarihli sınırlı değerlendirme, belirlenen literatür ve yöntem kapsamını
sınırlamalarla kapattı. On iki hipotezin dar yorumları için iki desteklenen, yedi
yeniden çerçevelenen ve üç kanıtı yetersiz sonuç kaydedildi. Bu sayılar ürünün başarı
oranı değildir; literatürün hangi iddiayı ne ölçüde taşıyabildiğini açıklar.

Değerlendirmede ayrı ajan incelemesi kullanıldı. Bu, kör insan değerlendirmesi,
kurumsal bağımsızlık veya dış deney tekrarı olarak sunulmaz. Sonraki kaynak ve gerçek
ortam çalışmaları, bu tarihli araştırma kararından ayrı kanıtlardır.

## Henüz cevaplanmamış ana fayda sorusu

Aynı görevlerde, aynı değerlendirme koşullarında, host/ajan akışı ile aynı akışa
mühendislik katmanı eklenmiş durumun doğru sonuç, toplam maliyet ve kullanıcı emeği
açısından karşılaştırılması gerekir. Mevcut sınırlı gözlem kalibrasyonu bu genel
karşılaştırmanın yerine geçmez.

Yalnızca başarılı denemeler sayılmaz; başarısızlık, onarım ve kontrollerin kendi ek
maliyeti de değerlendirmeye girer. Ölçülemeyen token veya fatura bilgisi tahminle
gerçek ölçüm gibi doldurulmaz.

## Kapsam düzeltmesi

PRAVECT'in her sağlayıcıya doğrudan API çağrısı yapan ayrı bir istemci olması gerekmiyor.
Araştırmanın odağı IDE içindeki ajan iş akışıdır. Doğrudan sağlayıcı API anahtarları
ve tüm sağlayıcılarda token kalibrasyonu genel çalışma önkoşulu değildir.

[Araştırma özeti](../evidence/RESEARCH_SUMMARY.md) · [ölçüm özeti](../evidence/CALIBRATION_SUMMARY.md)
