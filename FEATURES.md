# PRAVECT — Proje bağlamından doğrulamaya

**Görev niyeti, kodda gerçekleşen değişiklik ve sonucu destekleyen kanıt aynı mühendislik çerçevesinde değerlendirilir.**

Yapay zekâ ile yazılım geliştirmede yalnızca kod üretimi yeterli değildir. Proje kararlarının
korunması, görev kapsamının sınırlandırılması ve tamamlandığı bildirilen değişikliklerin
uygun kontrollerden geçmesi gerekir. PRAVECT; proje hedeflerini, görev sözleşmesini,
mühendislik kurallarını ve doğrulama bulgularını ilişkilendirmek için geliştiriliyor.

> **Durum (13 Ekim 2026):** Önceki geliştirme tabanının ön gösterimi. Bu tarihteki bütünleşme odağı **Windows + Codex**, arayüz **VS Code** idi. Sonraki eklenti merkezli yeniden tasarım kararı bu sürümde henüz uygulanmış değildir.
> Genel kullanıma sunulmuş kurulum paketi veya açık alfa programı yoktur. Görev kapsamının
> işletim sistemi düzeyinde korunması üzerinde çalışılıyor; hatasız yazılım garantisi verilmez.

## Kullanım alanları

- **Bağımsız geliştiriciler:** Proje kararlarının ve doğrulamaların izlenebilirliği.
- **Küçük ekipler:** Görev sınırlarının ve inceleme gerekçelerinin paylaşılması.
- **AI ile düzenli çalışan geliştiriciler:** Tekrarlanan bağlam aktarımının azaltılması.
- **Teknik olmayan proje sahipleri:** İstenen davranış ile gözlenen sonucun ayrılması.

## Temel yetenekler

### 1. Proje niyetinin yapılandırılması

Proje hedefleri ve kısıtları `ROADMAP.md` gibi belgelerden derlenir. Kaynağın ne olduğu,
hangi bilginin açıkça verildiği ve nerede çıkarım yapıldığı korunur. Eksik bilgi,
doğrulanmış gerçek gibi sunulmaz.

### 2. Plan ile gözlenen durumun ayrılması

Yol haritasında bir özelliğin tanımlanmış olması, o özelliğin kaynak kodunda uygulandığını
kanıtlamaz. PRAVECT, **VERIFIED / INFERRED / UNKNOWN** ayrımını kullanarak planları,
çıkarımları ve depo gözlemlerini birbirinden ayırmayı destekler.

### 3. Göreve uygun mühendislik kuralları

Yazım düzeltmesi ile veri taşıma işlemi aynı risk ve doğrulama gereksinimlerine sahip
değildir. Görev sınıfına göre ilgili kural paketleri seçilir; düşük riskli işler için
kontrollü, daha hafif bir yol öngörülür. Belirsizlik arttığında normal denetim akışı esas alınır.

### 4. Yapılacak işin sınırlarını belirleme

Bir işe başlamadan hangi dosyaların değiştirilebileceği, nelerin yalnızca okunabileceği
ve hangi durumda durulacağı belirlenir. Örneğin tarih filtresini düzeltme talebi,
veritabanını yeniden tasarlama izni vermez. Bu bilgiler görev sözleşmesinde tutulur.

### 5. Tamamlanan işi gerçekten doğrulama

Kontrollerin hangi kod değişikliği üzerinde yapıldığı kaydedilir. Dosya daha sonra
değiştirilirse eski test sonucunun hâlâ geçerli olduğu varsayılmaz. Başarılı bir
kontrol, yalnızca gerçekten sınadığı davranış için güvence sağlar.

### 6. VS Code arayüzü

Panel; çalışma alanını, Codex bağlantısını, hazırlık kontrollerini, gözlem ve ölçüm
işlemlerini bir araya getirmek üzere geliştirilmiştir. Bu sitedeki etkileşimli arayüz
**örnek JSON kayıtlarını gösterir**; gerçek Codex, Python veya VS Code işlemi başlatmaz.

## Örnek iş: sipariş iptalinin düzeltilmesi

1. **Amaç:** İptal edilen siparişin stok etkisi geri alınır; yinelenen iptal ikinci kez artışa yol açmaz; ödeme sistemi kapsam dışıdır.
2. **Gerçek durum:** Mevcut iptal akışı kaynak kodu üzerinden incelenir, varsayılmaz.
3. **Sınırlar:** Veri bütünlüğü kuralları, düzenlenebilir dosyalar ve gerekli kontroller belirlenir.
4. **Doğrulama:** Başarılı ve yinelenen iptal senaryoları sınanır.
5. **Değerlendirme:** İnceleme ve test sonuçları aynı değişiklik adayına bağlanır; eksik kanıt görünür kalır.

Bu, hedeflenen çalışma düzenini açıklayan bir senaryodur; hazır ve tek tıkla yürütülebilir bir iş akışı değildir.

## 13 Ekim 2026 tabanının durumu ve sınırları

**13 Ekim 2026 tabanında mevcut bileşenler:** Proje profilini düzenleme, ilgili kural içeriğini hazırlama,
görev sözleşmesi, aday ve inceleme bağları; VS Code paneli ve seçilmiş Codex
gözlem/ölçüm yolları. Gerçek IDE'deki sınırlı gözlem kalibrasyonu 16 çalıştırma
kapsamında tamamlanmıştır.

**13 Ekim itibarıyla tamamlanmamış çalışmalar:** Korunan doğrulama ve kanıt üretimi sınırı, uçtan uca host kabulü,
genel ürün faydası ölçümü ve farklı ortamlarda dağıtım. Ölçülmemiş bir hız veya tasarruf
oranı iddia edilmiyor.

**Gelecekteki genişletme:** Kod, proje niyeti ve ajan faaliyet geçmişinin ilişkili,
zamansal graph/vector mühendislik belleğiyle temsil edilmesi. **Henüz uygulanmadı.**

## Deney ve karşılaştırma

Önceki AI Engineer sürümüyle yürütülen MiniDesk üretimi ve bağımsız ürün karşılaştırması, eksik ölçümler ve yayın sınırlarıyla birlikte [MiniDesk deney özetinde](tests/README.md) belgelenmiştir. Bu sonuçlar yeni PRAVECT mimarisinin kabul testi değildir.

## İlgili belgeler

- [Ana sayfa](README.md) · [Özellik durumu](status/FEATURE_STATUS.md) · [Bilinen sınırlar](status/LIMITATIONS.md)
- [Geliştirme yol haritası](status/ROADMAP.md) · [Kanıt modeli](docs/EVIDENCE_MODEL.md)
- [Seçilmiş doğrulama özetleri](evidence/README.md) · [Mühendislik belleği hedefi](docs/ENGINEERING_MEMORY.md)

*Durum tarihi: 13 Ekim 2026. PRAVECT bağımsız bir projedir; adı geçen IDE ve model sağlayıcılarının resmî ürünü veya onayladığı entegrasyon değildir.*
