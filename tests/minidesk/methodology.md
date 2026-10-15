# MiniDesk — Deney ve karşılaştırma yöntemi

[Genel özet](../README.md) · [Sonuçlar](results.md) · [Sınırlamalar](limitations.md)

## 1. Üretim deneyinin niteliği

MiniDesk, önceden tanımlanmış [ROADMAP](evidence/selected/ROADMAP.md) gereksinimlerinden oluşturuldu. İnsan tarafından belirlenen gereksinimler hedefi tanımladı; Codex uygulamayı, testleri ve çeşitli süreç yardımcılarını üretti. Tarihsel adı AI Engineer olan kit görev sınırlandırması, kural bağlamı hazırlama, aday sabitleme ve kanıt/kabul kontrollerini sağladı. İmza işlemleri ve bağımsız değerlendirmeler insan katılımı gerektirdi.

Başlangıç temel sürümü **AI Engineer 2.1.1-rc.1** olarak raporlanmıştır; ilk gözlenen kurulumda `phasefix.1` vardı, süreçte `attestfix.1` de kullanıldı. Deney değiştirilmemiş bir rc.1 sürümünün bağımsız performans ölçümü olarak yorumlanamaz. Aşamalar M0–M4 olarak kaydedildi; son kabul edilen aday `cand-c9989cb5fa78c893` oldu. Teknik sonuç, adayın sabitlenmesi, inceleme ve insan kabulü birbirinden ayrı kayıtlandı.

Süreçte **311 kayıtlı komut** bulunur. Komut süresi, takvim süresi, ajan bekleme süresi, insanın etkin çalışması ve model token maliyeti aynı ölçüler değildir. Model token tüketimi, maliyet ve etkin insan süresi bu yayın kapsamındaki tarihsel verilerde **UNKNOWN** durumundadır. Yürütme ortamı, izin, test yardımcıları ve kural mekanizmaları kaynaklı sorunlar kanıtsız biçimde tek nedene atfedilmez.

## 2. İki ürünün karşılaştırması

**A — AI Engineer kullanılan ürün:** Python/Flask/SQLite.

- Özgün deney kaynak ZIP'i SHA-256: `854a411640a80904e3558ee9dbc9aaba3efa09698bb8a0c82cf07a50bef0d31f`.
- [Kamuya sunulan uygulama ZIP'i](applications/with-ai-engineer.zip) SHA-256: `446943a5f5c6d49a32cf7a7fa8114600e2a02b5d52b28093a58ecf44a718e211`.

**B — referans ürün:** Python `http.server`/SQLite.

- Özgün deney kaynak ZIP'i SHA-256: `db3c075e8fbb3f37e8901baf8fdf9f700bce8f956f1693d93b0f139b58b6d1ba`.
- [Kamuya sunulan uygulama ZIP'i](applications/without-ai-engineer.zip) SHA-256: `edc1afd2aa363e3d01b7a6ec51833944ac3a3107863183cafd76c10b3bf33aec`.

**Hash farklarının nedeni:** Kamu ZIP'leri ayrı dağıtım kopyalarıdır. Her iki arşivin `LICENSE` dosyasında daha önce boş bırakılmış telif bildirimi `PRAVECT` olarak tamamlandı; B arşivine özgün kaynak ZIP'inde bulunan, içerik hash'i `MANIFEST.json` ile eşleşen `ROADMAP.md` geri kondu. Diğer uygulama ve test dosyaları değiştirilmedi. Özgün deney kaynak hashleri tarihsel karşılaştırma için korunur; indirilmiş dosyanın bütünlüğünü kontrol etmek için **kamu ZIP'inin hash'i** kullanılmalıdır. Bu paketler geçmiş deneyin orijinal ZIP'leriyle bayt düzeyinde aynı değildir.

**Ortak gereksinimler:** [ROADMAP.md](evidence/selected/ROADMAP.md), SHA-256 `9d203e6f5c2bbff446ba4db7be09bae57f8c939e96e5bf898ac90f1667e99d97`.

Karşılaştırmada önceden belirlenen **48 ortak senaryo** ve **12 performans/kaynak ölçümü** kullanıldı. [Senaryo matrisi](evidence/selected/TEST_CASES.csv) kaynak protokoldeki test kapsamını korur; [sonuç matrisi](evidence/selected/COMMON_CASES.csv) sonuçların sonradan temkinli biçimde sınıflandırılmış durumunu içerir. Kaynak ürünlerin kendi test sayılarına üstünlük puanı verilmez. `TEST_CASES.csv` içindeki `side_a` ve `side_b` sütunları önceden dondurulmuş protokolün başlangıç durumlarını (`NOT_ASSESSED`) korur; **nihai test sonuçları değildir**. Gerçek sınıflandırma için `COMMON_CASES.csv` esas alınır. Tarihsel kaynak verisini değiştirmemek için iki dosya birleştirilmedi.

Karşılaştırma 100 puan üzerinden 11 alana ayrılmıştı: ROADMAP uyumu (15), işlevsel doğruluk (15), veri bütünlüğü (10), güvenlik (12), çalışma performansı (12), kaynak kullanımı (8), kod yapısı (8), test niteliği (7), arayüz/erişilebilirlik (6), kurulum/taşınabilirlik (4), belgeler (3). **Bu ağırlıklar sonucu hesaplamak için kullanılmadı:** kritik veriler eksikti.

`PASS` beklenen davranışın sınandığını, `FAIL` gerçekleşmiş ihlali, `BLOCKED` dış ortam engelini, `NOT_ASSESSED` yeterince denetlenmemiş durumu, `NOT_APPLICABLE` gereksinimlerin dışında kalmayı ifade eder. Bu sınıflar birbirine dönüştürülmedi. Örneğin HTML etiketinin bulunması, gerçek klavye kullanımını doğrulamaz; bir HTTP başlığının gözlemlenmesi de bütün güvenlik politikasının yeterli olduğu anlamına gelmez.

## 3. Deneme ortamı ve eksik ölçümler

Önceden belirlenmiş birincil ortam **Windows/CPython 3.11 (64 bit)**, aynı bilgisayar, aynı SSD ve güç ayarıydı. Mevcut karşılaştırmalı çalışma **Linux/Python 3.13.5** ortamında gerçekleştirildi ve yalnızca **ikincil doğrulama** olarak raporlandı. Gerçek Chromium gezinmesi ortam yöneticisi tarafından reddedildi. Windows temiz kurulum ve hedef tarayıcı kontrolleri yapılmadı.

Önceden belirlenen sentetik veri kümeleri boş veritabanı, 100 kayıt ve 1.000 kayıt düzeylerindeydi. HTTP süreleri için eşlenmiş tekrarlar ve p50/p95 istenmişti; başlatılan Linux denemeleri zaman sınırına takıldı. Tamamlanmamış sonuçlardan hız veya CPU/RAM üstünlüğü çıkarılmadı. Aynı mantıksal içerik için SQLite dosya boyutları ayrıca gözlemlendi.

## 4. Tekrarlanabilirlik ve yayınlanan kanıtlar

Seçilmiş kanıtlar: [ROADMAP](evidence/selected/ROADMAP.md), [48 önceden belirlenen senaryo](evidence/selected/TEST_CASES.csv), [96 ürün-senaryo sonucu](evidence/selected/COMMON_CASES.csv), [Python kapsam değerleri](evidence/selected/COVERAGE_METRICS.json), [eşdeğer veri kümesi denetimleri](evidence/selected/FIXTURE_CHECKS.json), [ek tanılamalar](evidence/selected/EXTRA_DIAGNOSTICS.json).

Bu seçim, yayımlanan bulguların önemli bir kısmını incelemeye imkân verir; tüm geçmiş komutlar, ham günlükler, özgün imzalı kabul kayıtları veya çalıştırılabilir test yürütücüsü burada bulunmaz. **Bu paket yeniden çalıştırılmış bir deney değildir; önceki kaynak kayıtlarından hazırlanmış sadeleştirilmiş kamu sunumudur.** [Kanıtların sınırları](limitations.md).
