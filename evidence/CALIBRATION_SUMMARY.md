# Gerçek IDE gözlem kalibrasyonu özeti

[Kanıt dizini](README.md)

> - **Durum:** COMPLETE_SCOPED (tanımlı kapsamda tamamlandı)
> - **Tarih:** 11 Ekim 2026
> - **Ortam / sürüm:** Windows + VS Code · Codex 0.162.0
> - **Kanıt düzeyi:** Sınırlı gerçek ortam kanıtı; test sınıfının oracle gücü PARTIAL
> - **Kanıtlar:** Native çalışma, gözlem, yapılandırma ve süre kayıtlarının tanımlı plana bağlanabildiğini.
> - **Kanıtlamaz:** Genel ürün etkinliğini, tasarrufu, tüm IDE maliyetini veya HostAuthority kabulünü.
> - **Kısaca:** Gözlem akışı tanımlı kapsamda tamamlandı; “PRAVECT daha hızlı” sonucu henüz yok.

| Alan | Açıklama |
|---|---|
| Kapanış tarihi | 11 Ekim 2026 |
| Ortam | Yerel Windows/VS Code, eklentinin sahip olduğu ayrı Codex App Server oturumu |
| Bildirilen sürüm ve hedef | Codex 0.162.0; donmuş hedef gpt-6.1-sol / high |
| Tasarım | Dört görev sınıfı; önceden belirlenmiş 16 slot / sekiz OFF/ON çifti |
| Sınıflar | Bağlam, sözdizimi, testler ve kontrollü hata |
| Beklenti | Tüm slotları korumak; görev, sonuç, oracle, yapılandırma ve zaman bağlarını değerlendirmek |
| Kayıtlı sonuç | COMPLETE_SCOPED; bütün slotlar yayımlandı, sekiz çift karşılaştırılabilir, tanımlı oracle kontrolleri geçti |

OFF/ON, ilgili gözlem mekanizmasının kapalı/açık durumlarını ifade eder. Bu deney
"PRAVECT olmadan geliştirme" ile "PRAVECT ile geliştirme" arasındaki genel ürün
etkinliği karşılaştırması değildir.

Kontrollü hata görevleri tasarımın parçasıdır; beklenen sıfır dışı dönüş kodları
başarısız örnekleri gizlemek için örneklemden çıkarılmamıştır. Önceki farklı aday ve
başarısız denemeler, bu donmuş planla birleştirilerek olumlu sonuca dönüştürülmemiştir.

## Ne gösterir?

Bu seçilmiş görevlerde native çalışma, gözlem, yapılandırma ve süre kayıtlarının
tanımlı plana bağlanabildiğine ilişkin sınırlı gerçek ortam kanıtı sağlar.

## Ne göstermez?

Bütün IDE'nin maliyetini, ürünün genel doğruluk/verimlilik etkisini, token/fatura
tasarrufunu veya kimliği doğrulanmış HostAuthority kabulünü göstermez. Test sınıfının
oracle gücü PARTIAL olarak kalmıştır. Tam ham sonuçlar bu pakette bulunmadığından
burada performans yüzdesi veya bağımsız yeniden üretilebilirlik iddiası sunulmaz.

## Dayanak kayıtları

Özel arşivde `144_full_plan_verification_2026-10-11/CLOSURE_DECISION.json`,
`PERSISTENT_EVIDENCE_REPORT.json` ve `EVALUATION.json`. Model/sürüm bilgisi tarihli
deney girdisidir; önerilen model veya ürünün kalıcı varsayılanı değildir.
