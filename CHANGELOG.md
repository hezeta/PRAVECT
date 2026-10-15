# Geliştirme değişiklikleri

[Ana sayfa](README.md) · Güncelleme: 16 Ekim 2026

PRAVECT henüz genel kullanıma yayımlanmış bir sürüm değildir. Bu kayıt, geliştirme
sürecindeki seçilmiş teknik gelişmeleri özetler; sürüm veya dağıtım duyurusu değildir.

## 16 Ekim 2026 — Yeniden tasarım yönü ve yayın belgeleri

- PRAVECT'in yeniden kuruluşu için hedef, depo içine kurulan altyapı yerine VS Code eklentisinin sahip olduğu yerel ve deterministik çekirdek olarak belirlendi. Bu **tasarım kararıdır**; yeni çekirdeğin geliştirildiğini veya doğrulandığını göstermez.
- PRAVECT'in ticari dağıtım ve lisanslama koşulları henüz duyurulmadı; bu kayıt herhangi bir ürün özelliği veya kullanım hakkı taahhüdü oluşturmaz.
- MiniDesk karşılaştırması, ölçülmemiş alanları ve başarısızlıkları görünür tutularak sadeleştirilmiş deney dizininde yayımlanmaya hazırlandı. İki örnek uygulamanın dağıtım ZIP'leri, kaynak hashlerinden ayrı belgelendi; referans uygulamada eksik ROADMAP geri kondu. MIT telif bildirimlerindeki hak sahibi adının hukuki doğrulaması açık kaldı.

## 13–15 Ekim 2026 — MiniDesk üretim deneyi ve karşılaştırma

- Önceki AI Engineer 2.1.1-rc.1 tabanlı, süreçte `phasefix.1` ve `attestfix.1` düzeltmelerinin kullanıldığı MiniDesk deneyi M0–M4 kabul kayıtlarıyla belgelendi.
- Aynı gereksinimlerden çıkan iki ürün için 48 ortak senaryo değerlendirildi; tarayıcı, hedef Windows ortamı ve yeterli performans ölçümü eksikleri nedeniyle genel kazanan açıklanmadı. [Deney özeti](tests/README.md).

## Ekim 2026 — IDE bütünleşmesi ve doğrulama çalışmaları (13 Ekim tabanı)

- VS Code arayüzü, Python köprüsü ve ayrı Codex oturumu için seçilmiş bağlantı ve gözlem yolları geliştirildi.
- Tanımlanmış 16 çalıştırma / sekiz OFF–ON çifti kapsamında gerçek IDE gözlem kalibrasyonu tamamlandı. Bu sonuç, genel verimlilik ya da maliyet avantajı kanıtı değildir.
- Windows host süreç ve dosya erişimi sınırında gözlemler yapıldı; son altı-hak incelemesinde seçilen erişimler reddedildi. Korunan doğrulayıcı ve uçtan uca host kabulü tamamlanmadı.

İlerleme ve açık sınırlar için [geliştirme günlüğü](devlog/README.md),
[özellik durumu](status/FEATURE_STATUS.md), [kanıt özetleri](evidence/README.md)
ve [bilinen sınırlar](status/LIMITATIONS.md) esas alınır.

Bu belgelerin yayımlanması; kaynak kodu, kurulum paketi veya açık alfa sürümü
yayımlandığı anlamına gelmez.
