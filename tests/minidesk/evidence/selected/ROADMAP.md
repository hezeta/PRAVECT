# MiniDesk — Yerel İş Talebi Yönetimi

> Durum: Deney için hedef ürün tanımı. Bu belge henüz uygulanmış veya doğrulanmış özellikleri değil, geliştirilmesi istenen davranışları belirtir.

## Product Goal

- P-01: MiniDesk, tek kullanıcının teknik iş taleplerini oluşturduğu, önceliklendirdiği, takip ettiği ve sonuçlandırdığı, yerel bilgisayarda çalışan bir web uygulamasıdır.
- P-02: Amaç; yalnızca görünüşü olan bir sayfa değil, gerçek veri kalıcılığı, HTTP API, iş kuralları, durum geçmişi, erişilebilir arayüz ve testleri bulunan küçük fakat bütünlüklü bir ürün geliştirmektir.
- P-03: İlk sürüm yalnızca tek bilgisayarda çalışır. İnternet bağlantısı, hesap açma veya haricî hizmet gerektirmez.

## Users and Roles

- U-01: Uygulamayı tek bir yerel operatör kullanır; bütün talepler için oluşturma, görüntüleme, düzenleme ve durum geçişi işlevleri aynı kişiye açıktır.
- U-02: Uygulama kişisel yerel araçtır; farklı kişilere ait hesapların yönetimi ve ortak kullanım desteklenmez.

## Functional Scope

- F-01: Her talep `id`, `title`, `description`, `priority`, `status`, `due_date`, `created_at`, `updated_at` alanlarını taşır. `id` sunucuda üretilen değişmez sayısal kimliktir; zaman damgaları UTC ISO-8601 biçimindedir.
- F-02: Başlık zorunludur (3–100 karakter). Açıklama isteğe bağlıdır (en çok 1000 karakter). Öncelik `low`, `normal`, `high` değerlerinden biridir; varsayılan `normal`dır. Son tarih isteğe bağlı `YYYY-MM-DD` biçimindedir.
- F-03: Yeni talep `todo` durumunda açılır. Kullanıcı başlık, açıklama, öncelik ve son tarihi daha sonra düzenleyebilir; kimlik ve oluşturulma zamanı değişmez.
- F-04: Durumlar `todo`, `doing`, `done` olarak tanımlanır. Geçerli geçişler yalnızca `todo -> doing`, `doing -> done` ve `done -> doing` (yeniden açma) şeklindedir. Durum alanı genel düzenleme çağrısıyla değiştirilemez.
- F-05: Talep listesinde başlık/açıklama içinde büyük-küçük harften bağımsız arama; durum ve öncelik filtreleri; son güncellenme zamanına göre en yeni önce sıralama bulunur. Filtreler birlikte uygulanabilir.
- F-06: Özet alanı toplam talep, açık talep (`todo` + `doing`), tamamlanmış talep (`done`) ve süresi geçmiş açık talep sayılarını gösterir. Son tarihi bugünden önce olan, `done` olmayan kayıt gecikmiş kabul edilir.
- F-07: Her oluşturma, düzenleme ve durum değişikliği için `events` geçmişinde zaman, işlem türü, talep kimliği ve değişen alanların önceki/yeni değerlerini içeren bir kayıt tutulur. Geçmiş yalnızca okunabilir.
- F-08: Kullanıcı talepleri JSON biçiminde dışa aktarabilir; dosya UTF-8 olur. İçe aktarma, veri silme ve toplu düzenleme bu deneyde bulunmaz.
- F-09: Sayfa yenileme ve sunucuyu kapatıp yeniden açma, kaydedilmiş talepleri veya geçmişlerini kaybettirmemelidir.

## Critical Workflows

- W-01: **Oluşturma:** Geçerli form gönderildiğinde tek talep ve ona bağlı `created` olayı aynı veritabanı işlemi içinde saklanır; arayüz liste ve sayaçları yeniler.
- W-02: **Düzenleme:** Yalnızca tanımlı dört alan değişebilir. Geçersiz alan veya değer reddedilir; reddedilen istekte kayıt ve geçmiş değişmemelidir.
- W-03: **Durum geçişi:** Geçiş sunucuda doğrulanır. Geçerli geçiş ile `status_changed` olayı atomik kaydedilir; yasak geçiş HTTP 409 döndürür ve hiçbir veri değiştirmez.
- W-04: **Kalıcı veri:** SQLite dosyası ilk çalıştırmada oluşturulur; sonraki açılışlarda korunur. Aynı isteğin başarısız olması veritabanını yarım yazılmış durumda bırakmamalıdır.
- W-05: **İstek doğrulama:** Bozuk JSON HTTP 400; kurala uymayan veri HTTP 422; olmayan kimlik HTTP 404; geçersiz durum geçişi HTTP 409 döndürür. API hataları kısa, tutarlı JSON hata nesnesiyle bildirilir.

## Data and Sensitivity

- D-01: SQLite veritabanında `items` ve `events` tabloları yeterlidir. `items.id` birincil anahtardır; `events.item_id` mevcut talebe bağlı yabancı anahtardır.
- D-02: Bütün veriler yerel diskte tutulur. Demo içeriği sentetik olmalıdır; gerçek ad, e-posta, erişim anahtarı veya müşteri verisi kullanılmaz.
- D-03: Veritabanı dosyası ve geçici dosyalar Git'e eklenmez. Uygulama başlangıç verilerini zorla yüklemez; ilk açılışta boş durum anlamlı biçimde gösterilir.
- D-04: Kayıt geçmişi uygulama arayüzünden değiştirilemez; dışa aktarma yalnızca talepleri kapsar. Otomatik saklama süresi ve yedekleme sistemi ilk sürümde yoktur.

## Integrations

- I-01: Tüm işlevler tek cihazdaki veritabanı ve tarayıcıyla çalışır; dış iletişim servisi veya başka bir sistem bağlantısı gerektirmez.
- I-02: Yerel HTTP API asgari olarak `GET /api/health`, `GET /api/items`, `POST /api/items`, `GET /api/items/<id>`, `PATCH /api/items/<id>`, `POST /api/items/<id>/transition`, `GET /api/items/<id>/events`, `GET /api/summary`, `GET /api/export` uçlarını sunar.
- I-03: Durum geçiş isteği `{ "status": "doing" }` biçimindedir. Liste sorgusu `q`, `status`, `priority` parametrelerini destekler; bilinmeyen parametrelerin işlenmesi zorunlu değildir.

## Client and UX Expectations

- UX-01: Türkçe arayüzde tek sayfa içinde özet kartları, arama/filtre alanı, talep listesi, talep oluşturma/düzenleme formu ve seçilen talebin işlem geçmişi bulunur.
- UX-02: Masaüstü (>=1024px) ve mobil (320–430px) genişliklerinde yatay sayfa taşması olmamalıdır. Mobilde tablo yerine okunabilir kart düzeni kullanılabilir.
- UX-03: Yükleniyor, liste boş, filtre sonucu yok, doğrulama hatası, sunucuya erişilemiyor ve işlem başarılı durumlarının anlaşılır karşılıkları bulunur.
- UX-04: Form etiketleri, görünür klavye odağı, semantik düğmeler ve hata metinleri bulunur; tüm temel işlemler yalnızca klavyeyle yapılabilir.
- UX-05: Kullanıcı girdileri DOM'a güvenli metin olarak yerleştirilir; kullanıcı tarafından sağlanan HTML çalıştırılmaz.

## Operational Expectations

- O-01: Uygulama Windows üzerinde Python 3.11+ ile yerel olarak başlatılır ve yalnızca `127.0.0.1` adresine bağlanır; varsayılan port 8000'dir.
- O-02: Flask (3.x) HTTP katmanı, Python standart kütüphanesindeki `sqlite3` veri katmanı, düz HTML/CSS ve çatı kullanmayan JavaScript istemcisi tercih edilir. Derleme adımı ve ücretli servis gerekmemelidir.
- O-03: Çalıştırma yönergesi `README.md` içinde bulunur. Hedef kullanım: sanal ortamda bağımlılığı yüklemek, `python app.py` ile başlatmak ve tarayıcıdan yerel adrese erişmek.
- O-04: `python -m unittest discover -s tests -v` komutu ağ bağlantısı olmaksızın otomatik testleri çalıştırmalıdır. Testler geçici SQLite veritabanı kullanmalı, gerçek kullanıcı verisini değiştirmemelidir.
- O-05: Uygulamanın kaynak dosyaları küçük modüllere ayrılır; hedef yaklaşık 8–12 uygulama/test dosyasıdır. Gereksiz katman, kod üretimi, mikroservis veya ek servis kurulumu istenmez.

## Constraints and Explicit Preferences

- C-01: İş kuralları yalnızca JavaScript tarafında uygulanmamalı; API katmanında da doğrulanmalıdır.
- C-02: Yerel prototip genel ağ servisi olarak tanıtılmamalıdır; varsayılan bağlama adresi dış ağlara açılmamalıdır.
- C-03: Düzeltme ve geliştirmeler kısa, kapsamı belirli aşamalarla yürütülebilmelidir; sonraki aşama öncekinin testlerini bozmamalıdır.
- C-04: Bağımlılık sayısı düşük tutulur. React, TypeScript derleme araçları, Docker, Redis ve haricî bileşen kütüphaneleri kullanılmaz.
- C-05: Tasarım gösterişli olmak zorunda değildir; okunabilirlik, durumun doğru gösterilmesi, temel erişilebilirlik ve tutarlı hata davranışı önceliklidir.

## Non-goals

- N-01: Çok kullanıcılı erişim, kimlik doğrulama, roller, gerçek müşteri verileri, internetten yayın ve kurumsal güvenlik sertifikasyonu hedeflenmez.
- N-02: Dosya yükleme, e-posta bildirimi, gerçek zamanlı WebSocket, arka plan görev kuyruğu, yapay zekâ bütünleşmesi ve üçüncü taraf API bağlantısı hedeflenmez.
- N-03: Veri içe aktarma, kalıcı silme, gelişmiş rapor grafikleri, sürükle-bırak pano ve mobil uygulama hedeflenmez.
- N-04: Yük testi, yüksek eşzamanlılık, çok sunuculu dağıtım ve veritabanı göç sistemi bu deneyin konusu değildir.

## Known Risks

- R-01: Aynı talebin yakın zamanda iki kez değiştirilmesi durumunda son yazan kazanır; eşzamanlı güncelleme çatışması çözümü ilk sürümün sınırıdır.
- R-02: Yerel SQLite dosyasının elle silinmesi veya bozulması veri kaybına yol açabilir; otomatik yedekleme yoktur.
- R-03: Tarayıcı-API iletişiminin kesilmesi işlem sonucunun belirsiz görünmesine yol açabilir; arayüz başarısız isteği başarılı ilan etmemelidir.
- R-04: Yerel prototip kimlik doğrulamasına sahip olmadığından cihazın güvenilmeyen ağ arayüzlerine açılması risklidir.

## Milestones

- M0 — **İskelet:** Çalışan Flask yerel sunucusu, boş HTML arayüz, SQLite ilk kurulum, `GET /api/health`, kurulum/başlatma belgeleri.
- M1 — **Talep yönetimi:** Veri doğrulama, oluşturma/listeleme/tekil görüntüleme/düzenleme API'leri; kullanıcı formu ve listesi; kalıcılık testleri.
- M2 — **İş akışı ve izlenebilirlik:** Geçerli durum geçişleri, yasak geçiş reddi, işlem geçmişi, atomik yazım; ilgili API ve birim testleri.
- M3 — **Görünürlük:** Arama ve filtreler, özet sayaçları, gecikme mantığı, JSON dışa aktarma; mobil uyum ve hata/boş durumları.
- M4 — **Tamamlama:** Otomatik testler, klavyeyle kullanım denetimi, README kullanım örneği, kabul senaryosu ve bilinen sınırlamaların belgelendirilmesi.

## Definition of Success

- S-01: Kullanıcı yerel sunucuyu başlatıp tarayıcıda yeni talep açabilir; düzenleyebilir, geçerli durum geçişleri yapabilir ve geçmişini görebilir.
- S-02: Yasak `todo -> done` geçişi HTTP 409 üretir; kayıt ve geçmişi değiştirmez. Geçersiz boş başlık HTTP 422 üretir.
- S-03: Birden fazla talepte arama, durum ve öncelik filtreleri birlikte doğru çalışır. Tamamlanan kayıt gecikmiş açık talep sayısına girmez.
- S-04: Uygulama durdurulup yeniden açıldığında talepler ve işlem geçmişi korunur; geçici test veritabanı gerçek veriyi etkilemez.
- S-05: En az 10 otomatik test; geçerli/geçersiz oluşturma, güncelleme, izinli/yasak geçiş, geçmiş, filtreler, özet, yeniden açılışta kalıcılık ve API hata kodlarını kapsar. Bütün testler başarılı olmalıdır.
- S-06: 390px ve 1280px ekranlarda temel işlemler yatay taşma olmadan yapılabilir; yalnızca klavyeyle form gönderme ve kayıt seçme mümkündür.
- S-07: README kurulum ve çalıştırma komutlarıyla deneyin kapsamını açıklar; sonuçlar gerçek test çıktılarıyla belgelenir, uygulanmamış işlevler tamamlandı diye işaretlenmez.
