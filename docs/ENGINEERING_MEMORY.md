# İleriye dönük hedef: zamansal mühendislik belleği

[Ana sayfa](../README.md) · Hedefin kayıt tarihi: 13 Ekim 2026

**Mevcut eklenti tamamlandıktan sonra ele alınacak kapsam genişletmesi. Uygulama başlamadı.**

PRAVECT için bir sonraki geliştirme yönlerinden biri, projenin teknik gerçekliğini,
niyetini ve gözlenebilir ajan faaliyetlerini graph ve vector tabanlı bir mühendislik
belleğinde ilişkilendirmektir. Bu hedef mevcut sürümün çalışan özelliği değildir;
bugünkü geliştirme ve kabul işlerinin tamamlanmasının önkoşulu da değildir.

## Birbirine bağlanacak üç alan

| Alan | Hedeflenen bilgi |
|---|---|
| Teknik gerçeklik | Kaynak dosyaları, semboller, bağımlılıklar, mimari ilişkiler ve revizyonlar arasındaki değişiklikler |
| Proje niyeti | ROADMAP, gereksinimler, görev sözleşmeleri, mühendislik politikaları ve beklenen davranış |
| Ajan faaliyeti | Erişilebilen görev başlangıçları, işlemler, dosya değişiklikleri, doğrulamalar, hatalar ve sonuçlar |

Amaç, kopuk günlüklerin ötesinde, bilginin hangi kaynak ve zamana ait olduğunu
koruyarak ilişkili bir geçmiş oluşturmaktır. Örneğin "Bu dosya hangi görev kapsamında
değişti, hangi gereksinime bağlıydı ve hangi doğrulama sonucu o revizyona aitti?"
sorusuna dayanaklarıyla ulaşabilmek hedeflenir.

Bu örnek hedeflenen sorguyu anlatır; bugün çalışan bir özellik gösterimi değildir.

## Graph ve vector farklı işlere hizmet edecek

**Graph**, varlıklar ve açık ilişkiler için yapısal temsil sağlayacak şekilde
değerlendirilecek. Görev, gereksinim, dosya, değişiklik ve doğrulama sonucu arasındaki
bağların zaman içindeki gelişimi izlenmek isteniyor. Birlikte veya ardışık gerçekleşen
olaylar, dayanak olmadan neden-sonuç ilişkisi olarak etiketlenmeyecek.

**Vector**, anlam bakımından ilgili bilgi ve geçmiş bağlam adaylarını bulmak için
değerlendirilecek. Benzer bir kaydın bulunması, onun doğru, güncel veya yetkili olduğu
anlamına gelmeyecek; kaynak ve revizyon bağları korunacak.

**Deterministik çözümleme**, açıkça modellenmiş ilişkiler üzerinde mümkün olan
sorgu ve kontrolleri yeni üretken model çağrıları olmadan yürütmeyi hedefleyecek.

**Bağlam yönetimi**, göreve özgü bilgiyi seçmeyi, tekrarları elemeyi ve gerektiğinde
kaynağına geri dönülebilen bir gösterim hazırlamayı amaçlayacak. Zorunlu mühendislik
ve güvenlik bilgisini kaybeden sıkıştırma başarı sayılmayacak.

## Token maliyeti hedefi nasıl anlaşılmalı?

Hedef, mümkün olan kayıt, çözümleme ve geri çağırma işlemlerini **ek üretken model
çağrısı gerektirmeden** yerel yürütmektir. "Bütün sistem sıfır maliyetlidir" veya
"Codex'e verilen bağlam token tüketmez" iddiası değildir.

- Yerel veri işleme, indeksleme ve sorgulama CPU/GPU, bellek ve disk kullanabilir.
- Embedding üretimi ve güncellemesi için yöntem henüz seçilmedi. Yerel çalıştırma ile
  harici hizmet kullanımı farklı kaynak, mahremiyet ve maliyet koşulları doğurur.
- Geri çağrılan bilgi modele gönderildiğinde model bağlamının bir parçası olur.
- Model tabanlı özetleme veya ek model çağrısı gerekip gerekmediği henüz kararlaştırılmadı.

Bu aşamada ölçülmüş token tasarrufu veya sıfır ek token garantisi verilmez.

## Kapsam ve açık kararlar

Bu yön, yalnız bir sohbet arama sistemi eklemekten daha geniştir; kodu, amacı ve
faaliyet geçmişini ilişkilendiren zamansal bir mühendislik bilgi sistemi hedefidir.
Ancak "tüm süreci kayıt altına alma" amacı, görünmeyen olaylara erişim garantisi
değildir. Toplanabilen olaylar, eksik kayıtlar ve veri izinleri açıkça gösterilmelidir.

Graph veritabanı, ontoloji, embedding modeli, vektör indeksi, güncelleme stratejisi,
saklama politikası ve yerel/uzak çalışma düzeni henüz seçilmedi. **TypeDB dahil hiçbir
veritabanı bu hedef için kesinleştirilmiş değildir.** Başka projelerdeki tercihler
PRAVECT'e otomatik aktarılmaz.

Belleğe yazılan bilgi, yeni bir talimat veya işlem yetkisi sayılmayacak. Bu katman,
mevcut görev, aday, politika ve kanıt bağlarını kullanacak şekilde değerlendirilecek;
doğrulayıcı ve yetki sınırlarının yerine geçmeyecek.

## Ne zaman ele alınacak?

Mevcut eklentinin kararlaştırılmış kapsamı tamamlandıktan sonra gerçek olay ve veri
yolları üzerinden ayrıntılı kapsamlandırma yapılacak. Ardından sınırlı prototip ve
uygun doğrulamalar için ayrı uygulama kararı verilecek. Bugünkü HOST ve sonraki
değerlendirme sırası değişmedi; bu hedef için yayımlanma tarihi belirlenmedi.

[Yol haritası](../status/ROADMAP.md) · [araştırma](RESEARCH.md) · [kanıt modeli](EVIDENCE_MODEL.md)
