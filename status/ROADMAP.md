# Geliştirme yönü

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

Bu yol haritası **13 Ekim 2026 tarihli önceki çalışma sırasını** açıklar; sonradan kararlaştırılan VS Code eklentisi merkezli yeniden kuruluş planı değildir. Takvim, sürüm çıkış tarihi veya
tamamlanma yüzdesi vaat etmez. Bir aşamanın sonucu, sonraki adımın kapsamını etkileyebilir.

## Mevcut temel

Mühendislik çekirdeğinin bağlam, politika, görev, aday, inceleme ve kurulum araçları
mevcuttur. VS Code paneli ve seçilmiş Codex akışları uygulanmıştır. Gerçek IDE
gözlem kalibrasyonu, tanımlı 16 slot ve sekiz çift kapsamında tamamlanmıştır.

## 13 Ekim itibarıyla yürütülen çalışma: korunan yürütme ve doğrulama sınırı — HOST

Görev kodunun doğrulayıcıya ve kanıt üreticisine hangi yollardan erişebildiği
inceleniyor. Son süreç erişim gözleminde altı hak reddedildi; daha önceki başka
bir süreç örneğinde gözlenen bellek okuma erişimi bulgusu kapanmış sayılmıyor.

Sonraki çalışma, ürüne ait geçici çocuk süreçte oluşturma izinlerinin ve meşru
iletişim/temizleme yolunun uygulanabilirliğini değerlendirmektir. Ayrı bir süreç
başlatmak tek başına yeterli görülmez; parent, IPC, thread/token, kod yükleme ve
aday dosyası yolları da gerekli kapsamda ele alınır.

Bu aşama gerçek otorite bağlantısı, kullanılan işlem yollarının denetimi ve
sürüm değişimlerinde gerekli yeteneklerin kontrol edilmesini kapsar. Her Codex
güncellemesinin sorunsuz çalışacağına dair garanti verilmez.

## Ardından

| Sıra | Amaç | Henüz ileri sürülmeyen sonuç |
|---|---|---|
| V01 — bağımsız değerlendirme | Belirli adayın uygun inceleme ve kabul koşullarıyla değerlendirilmesi | Genel veya dışarıdan bağımsız kabul tamamlandı iddiası |
| B01 / IP05.9 — etkinlik | Aynı görev koşullarında doğru sonuç ve toplam iş maliyetinin karşılaştırılması | Ölçülmüş genel verimlilik/tasarruf |
| R01 — risk | Kontroller, hata biçimleri ve kalan risklerin değerlendirilmesi | Sıfır risk veya her saldırıya karşı koruma |
| X01 — dış doğrulama | Uygun önkoşullarla geliştirme ortamı dışındaki kullanımın değerlendirilmesi | Açık alfa/beta programının başlamış olması |

## Mevcut eklenti tamamlandıktan sonra: mühendislik belleği

Kapsam genişletmesi; teknik gerçeklik,
proje niyeti ve gözlenebilir ajan faaliyetlerini zamansal graph ile ilişkilendirmek,
vector üzerinden anlamsal geri çağırmayı ve mümkün olan deterministik çözümlemeyi
desteklemektir. **Uygulama başlamadı; veritabanı ve embedding yöntemi seçilmedi.**

Önce mevcut eklenti kapsamı tamamlanacak, ardından bu hedef ayrıntılandırılarak ayrı
uygulama kararı verilecek. Yeni hedef yukarıdaki kapanışların ek önkoşulu değildir.
Ek üretken model çağrılarını azaltmak hedeflenir; sıfır toplam maliyet veya ölçülmüş
token tasarrufu iddia edilmez. [Ayrıntılı hedef](../docs/ENGINEERING_MEMORY.md).

Araştırmada ele alınan diğer yöntemler, örneğin model router'ı veya yeni servis,
kendiliğinden ürün yol haritasına eklenmez.

[Bilinen sınırlar](LIMITATIONS.md) · [geliştirme günlüğü](../devlog/README.md)
