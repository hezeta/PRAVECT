# Görev sözleşmesi

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

Görev sözleşmesi, yapılacak işin kapsamını ve değerlendirme koşullarını açık hâle
getiren yapılandırılmış kayıttır. Bir planın yazılmış olmasıyla görevin başarıyla
tamamlanmış olması farklı durumlardır.

## Neleri kapsar?

- Amaç ve değişiklik sınıfları.
- Yazılabilir, salt okunur ve yasak alanlar.
- İlgili politika paketleri.
- Kabul ölçütleri ve gerekli doğrulamalar.
- Onarım sınırı ve durma koşulları.
- Dış etkiler için gereken açık yetkilendirme bilgisi.

Mevcut üretici, kendisine verilen yapılandırılmış görev girdisinden sözleşme oluşturur.
Değişiklik sınıflarını politika paketleri ve doğrulama gereksinimleriyle eşleştirir;
bilinmeyen sınıfları reddeder. Doğal dildeki her isteğin sınıfını tek başına doğru
belirlediği iddia edilmez.

## İşin büyüklüğüne uygun süreç

Kaynakta belge odaklı ve düşük riskli küçük değişiklikler için daha hafif doğrulama
yolları bulunur. Bunların seçimi yalnızca ajanın "küçük değişiklik" beyanına dayanmaz.
Makine bulguları yeterli değilse NORMAL yoluna dönülür. Küçük bir diff, güvenlik
etkisinin küçük olduğunu kendiliğinden kanıtlamaz.

## Adayı dondurmak

Dondurma, incelenecek dosya içeriklerini ve görev bağlarını belirli bir kayda bağlar.
Desteklenen Git durumlarında revizyon/diff/içerik tutarlılığı da kontrol edilir.
Sonradan değişen bir aday için eski doğrulama sonucu otomatik olarak geçerli sayılmaz.

Bu mekanizma bir yedekleme sistemi veya tüm depoyu değiştirilemez kılan OS koruması
değildir. Mevcut düzenli-dosya dondurucusunun silme, submodule ve bazı Git dönüşümleri
gibi açık kapsam sınırları vardır.

## İnceleme ve yetki

İnceleme araçları uygulayan ve inceleyen rollerin ayrılmasını, ilgili görev/aday
bağlarını ve risk sınıfına uygun şartları kontrol eder. Kimlik alanlarının doldurulması
gerçek kimlik doğrulaması değildir; güvenilir üretici bağlantısı ayrıca gerekir.

Sözleşmede bir işlemin yazılı olması, kendi başına işletim sistemi yetkisi vermez.
Makine/host uygulaması ile belge düzeyindeki yönlendirme ayrı değerlendirilir.

[Kanıt modeli](EVIDENCE_MODEL.md) · [mimari](ARCHITECTURE.md)
