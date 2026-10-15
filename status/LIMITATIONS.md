# Bilinen sınırlar

[Ana sayfa](../README.md) · Durum: 13 Ekim 2026

## Kullanılabilirlik ve dağıtım

Bu ön gösterim teknik belgeler ve örnek kayıtlarla çalışan bir arayüz temsili içerir.
Kaynak kodu, eklenti kurulum paketi, destek taahhüdü veya açık alfa programı sunulmaz. Prototipin geliştirildiği ortamda çalışması, farklı kullanıcı
ortamlarında dağıtım kabulünün tamamlandığı anlamına gelmez.

## Otomasyon ve IDE bağlantısı

Çekirdekteki araçların varlığı, her doğal dil görevinin bütün adımlarını kendiliğinden
yürüten bir sistem olduğu anlamına gelmez. Ajanın/kullanıcının hazırladığı girdiler
ve başlattığı adımlar bulunur. IDE adaptörlerinin uyguladığı sınırlar eşdeğer değildir.

AI Engineer'ın ayrı Codex oturumu ile resmî Codex sohbeti farklıdır. Panelde seçilen
hedef, resmî sohbetin modelini otomatik değiştirmez. Hook gözlemi etkin sekme veya
canlı yürütme yetkisi değildir. Mevcut yerel kurulumda hook güveni kullanıcı tarafından
manuel işaretlenmiştir; bu işlem otomatik kurulum özelliği olarak sunulmaz.

## Güvenlik ve kabul

Korunan doğrulayıcı ve gerçek HostAuthority bağlantısı tamamlanmamıştır. Hash,
zaman damgası, süreç/oturum kimliği ve yerel JSON kayıtları tek başına kimliği
doğrulanmış kanıt üretmez. Dosya koruması, süreç/iletişim korumasının yerine geçmez.

Son altı-hak matrisi yalnız ilgili süreç örneğini ve istenen hakları kapsar. Ağ,
thread/token, bütün native araçlar ve kod yükleme yolları için toplu kabul değildir.
Önceki başarısız kayıtlar geçerli tarihsel bulgular olarak korunur.

## Ölçüm ve araştırma

Sınırlı OFF/ON gözlem kalibrasyonu genel ürün etkinliği deneyinden farklıdır. Token,
fatura, tüm IDE maliyeti veya kullanıcı verimliliği için ölçülmemiş yüzdeler verilmez.
Yerel testler gerçek ortam kabulü, literatür desteği de ürün faydası kanıtı değildir.

## Kaynak ve revizyon işlemleri

Mevcut aday dondurma mekanizması değişen düzenli dosyaları bağlar; tüm depoyu
dondurmaz. Silme/submodule ve bazı Git filtre/dönüşüm durumları destek sınırıdır.
Git bulunmayan işlerde Git revizyon kanıtı bilinmeyen kalır; NORMAL çalışma yolu
korunur. Kurulum kurtarması da tüm depolama arızalarını kapsayan bir garanti değildir.

## İleriye dönük mühendislik belleği

Graph/vector mühendislik belleği mevcut eklenti sonrası hedeftir. Henüz veri toplama,
graph/vector indeksleme veya bu katman üzerinden bağlam üretimi uygulanmış değildir.
TypeDB veya embedding yöntemi seçilmemiştir. Yerel çalışma, toplam hesaplama maliyetini
ve modele gönderilen bağlamın token kullanımını sıfırladığı iddiası taşımaz.

## Yayınlanan kanıtların sınırı

Bu pakette özetler bulunur; tam kaynak adayı, ham loglar ve yeniden üretim ortamı
sunulmaz. Ayrı ajan incelemesi dış bağımsız denetim veya kör insan değerlendirmesi
olarak adlandırılmaz. [Kanıt modeli](../docs/EVIDENCE_MODEL.md).
