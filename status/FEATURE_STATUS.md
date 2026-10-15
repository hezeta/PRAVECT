# Özelliklerin mevcut durumu

[Ana sayfa](../README.md) · 13 Ekim 2026 tarihli görünüm

Bu tablo kaynak incelemesi ve tarihli geliştirme kayıtlarının özetidir. Bu tanıtım
hazırlanırken ürün testleri yeniden çalıştırılmamıştır. "Uygulanmış" etiketi bütün
ürünün gerçek kullanıcı ortamında kabul edildiği anlamına gelmez.

| Alan | Mevcut durum | Sınır |
|---|---|---|
| SYSTEM / USER | Ortak kurallar ve proje bilgisi ayrımı mevcut | Mantıksal ayrım tek başına OS koruması değil |
| ROADMAP derleme | Yapılandırılmış ara gösterim ve proje profili üreticisi mevcut | Türetilmiş niyet, depoda gözlenen gerçek durum değil |
| Depo keşfi | Kanıta bağlı durum ve araç zinciri keşif araçları mevcut | Dosya/dependency varlığı aktif mimariyi tek başına kanıtlamaz |
| Politika bağlamı | Seçilmiş paketleri gerçek kural içeriğine derleyen araç mevcut | Her göreve doğru paket seçimi kendiliğinden garanti değil |
| Görev sözleşmesi | Sınıf, kapsam, kontrol ve yetki gereksinimlerini yapılandırıyor | Yapılandırılmış girdi gerekiyor; genel doğal dil orkestrasyonu değil |
| Doğrulama yolları | Makine bulgularıyla hafif veya NORMAL yol seçimi mevcut | Belirsiz durumda NORMAL; genel semantik eşdeğerlik çözümü değil |
| Aday/revizyon bağlama | Dosya, görev ve desteklenen Git durumları için kontroller mevcut | Tüm depo snapshot'ı değil; silme/submodule ve bazı dönüşümler kapsam dışı |
| İnceleme ve kanıt araçları | Görev/adayı bağlama ve rol/kabul kontrolleri mevcut | Gerçek güvenilir üretici/kimlik bağlantısı tamamlanmadı |
| Kurulum/kurtarma | İşlem günlüğü, upgrade, rollback, recovery ve bütünlük kontrolleri mevcut | Bu ön gösterimde dağıtılmıyor; her depolama arızası için garanti değil |
| VS Code paneli | Yerel panel, kontroller, bildirimler ve sonuç ayrıntıları mevcut | Harici temiz kurulum ve genel kullanıcı kabulü tamamlanmadı |
| Ayrı Codex bağlantısı | Owned App Server, hedef seçimi ve sınırlı native akış mevcut | Resmî Codex sohbetini devralma/senkronize etme değil |
| Oturum gözlemi | Seçilmiş kayıt/hook ve yürütme gözlem araçları mevcut | Son gözlem etkin sekme veya tüm IDE telemetrisi değil |
| OFF/ON kalibrasyon | Gerçek VS Code ortamında 16 slot / sekiz çift sınırlı kapanış | Genel etkinlik, tasarruf veya tüm IDE maliyeti değil |
| HOST koruma sınırı | Dosya/süreç tanıları mevcut; gerçek erişim bulguları elde edildi | Korunan doğrulayıcı, IPC/loader/otorite zinciri açık |
| Genel fayda değerlendirmesi | Araştırma ve ölçüm sözleşmeleri mevcut | Karşılaştırmalı ürün faydası sonucu henüz yok |
| Graph/vector mühendislik belleği | Mevcut eklenti sonrası hedef olarak kaydedildi | Uygulama başlamadı; teknoloji ve maliyet modeli seçilmedi |

Codex, Claude Code, Cursor ve Copilot için kaynakta farklı adaptör yüzeyleri vardır.
Bir adaptörün bulunması aynı panelin, aynı yaptırımın veya eşdeğer gerçek ortam
desteğinin bütün bu ürünlerde mevcut olduğu anlamına gelmez.

[Mimari](../docs/ARCHITECTURE.md) · [yol haritası](ROADMAP.md) · [kanıtlar](../evidence/README.md)

[Mühendislik belleği hedefi](../docs/ENGINEERING_MEMORY.md) mevcut özelliklerden ayrı,
ertelenmiş bir kapsam genişletmesidir.
