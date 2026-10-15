# Mimari ve işleyiş

[Ana sayfa](../README.md) · **Önceki mimarinin 13 Ekim 2026 tarihli açıklaması**. Yeni PRAVECT tasarımının doğrulanmış uygulaması değildir.

## Mühendislik çekirdeği

Ürün Python ağırlıklı bir mühendislik çekirdeğine ve onun üzerindeki IDE bağlantılarına
dayanır. VS Code paneli çekirdeğin yerine geçen ikinci bir politika motoru değildir.

| Katman | Sorumluluğu |
|---|---|
| SYSTEM | Ortak mühendislik kuralları, kontrol tanımları, şemalar ve bütünlük bilgileri |
| USER | Projeye özgü niyet, profil, gözlenen durum, karar ve kanıt kayıtları |
| Python araçları | Derleme, keşif, görev/adayı bağlama, doğrulama ve raporlama işlemleri |
| IDE adaptörleri | Ortak çekirdeğe ulaşmak için ortama özgü talimat ve entegrasyon yüzeyleri |
| VS Code eklentisi | Panel, çalışma alanı ve interpreter seçimi, işlemler ve süreç yaşam döngüsü |
| Owned native bağlantı | Eklentinin başlattığı ayrı Codex App Server oturumuyla seçilmiş işlemler |

SYSTEM/USER ayrımı ortak mühendislik yetenekleriyle proje bilgisini ayırır. Bu
mantıksal ayrım, tek başına işletim sistemi seviyesinde değiştirilemezlik kanıtı değildir.

## Çekirdeğin desteklediği akış

```text
Proje hedefleri / ROADMAP
  → yapılandırılmış proje profili
  → depoda gözlenen durum
  → görev sınıfı ve ilgili politika bağlamı
  → görev sözleşmesi
  → uygulama ve değişiklik kaydı
  → doğrulama yolu ve aday dondurma
  → inceleme, kanıt değerlendirmesi ve sonuç
```

Bazı girdiler ajan veya kullanıcı tarafından hazırlanır; araçlar bunları işler ve
denetler. Bütün doğal dil yorumlama ve araç çağırma adımları tek bir otomatik
orkestrasyon sistemi tarafından yürütülüyor olarak sunulmaz.

## IDE içinde üç farklı bağlantı

1. **Python köprüsü:** Seçilmiş yerel araçları sınırlı alt süreç çağrılarıyla çalıştırır.
   Normal bir alt süreç başlatmak, onu korumalı doğrulayıcı yapmaz.
2. **Ayrı Codex oturumu:** AI Engineer'ın sahip olduğu App Server bağlantısıdır.
   Mevcut resmî Codex sohbetini devraldığı veya onun model seçimini değiştirdiği
   anlamına gelmez.
3. **Oturum gözlemi:** Seçilmiş kayıtlar ve hook olayları üzerinden bilgi toplar.
   Son gözlenen oturum, etkin sohbet sekmesinin veya canlı bağlantının kesin kimliği değildir.

## HOST ile ne kastediliyor?

VS Code'un **Extension Host** süreci eklentilerin çalıştığı süreçtir. PRAVECT
çalışmalarındaki **HOST sınırı** ise görevin hangi yetkilerle çalıştığını, doğrulayıcı
ve kanıt üreticisinin görev kodundan nasıl korunduğunu kapsayan daha geniş sorumluluktur.

Mevcut `HostAuthority` arayüzü, kanıt üreticisinin kimliği ve görev/aday/kontrol
bağlarının doğrulanmasını bekler. Gerekli gerçek otorite bulunmadığında kabul
desteklenmiyor veya engelleniyor olarak kalır. Yerel JSON, hash veya süreç kimliği
kendi başına bu otoritenin yerine geçmez.

## Mevcut sınır

Korunan doğrulayıcı ve ona ulaşan süreç, iletişim, kod yükleme ve dosya yollarının
birlikte doğrulanması sürmektedir. İzinleri daraltılmış ayrı bir çocuk süreç aday
yaklaşımdır; tamamlanmış mimari çözüm olarak kabul edilmemiştir.

Ürün çalışma zamanı araştırma arşivine bağımlı olacak şekilde tasarlanmamalıdır.
Arşiv karar ve doğrulama geçmişini taşır; ürün mekanizmalarının sahibi kaynak ağacıdır.

[Bilinen sınırlar](../status/LIMITATIONS.md) · [görev sözleşmesi](TASK_CONTRACT.md)
