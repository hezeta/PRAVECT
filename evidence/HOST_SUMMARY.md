# HOST erişim gözlemleri özeti

[Kanıt dizini](README.md) · Durum: 13 Ekim 2026

> - **Durum:** OBSERVED (son gözlemde altı hakkın altısı DENIED); önceki süreç koruma kontrolü FAIL olarak korunuyor
> - **Tarih:** 13 Ekim 2026
> - **Ortam / sürüm:** Windows + VS Code · Codex 0.162.0-alpha.17.2 (ilk gözlem)
> - **Kanıt düzeyi:** UNAUTHENTICATED_DIAGNOSTIC · host_acceptance: NOT_ASSESSED
> - **Kanıtlar:** İki ayrı süreç örneğinde, istenen erişim haklarının verilip verilmediğini.
> - **Kanıtlamaz:** Korunan doğrulayıcının tamamlandığını; thread/token, IPC, loader ve ağ için kabul yoktur.
> - **Kısaca:** Altı ret, çalışmaya devam etmek için dar ve olumlu bir bulgu; sorun kapanmış değil.

Bu kayıt, korunan doğrulayıcı çalışmasının neden devam ettiğini gösterir.

## İlk gözlem: dosya sınırı ile süreç sınırı farklı

Yerel Windows/VS Code ortamında Codex `0.162.0-alpha.17.2` ve yapılandırılmış elevated
sandbox ile yapılan sabit tanıda izin verilen çalışma alanı yazması ve korunan dosya/
dizin yazma retleri geçti. Extension Host için VM_READ isteyen handle verildiği için
süreç koruma kontrolü FAIL kaldı.

Gerçek worker token'ındaki ortak oturum SID'si ile hedef süreç izinleri, bu erişimle
uyumlu somut bir izin yolu gösterdi. Handle kullanılmadan kapatıldı; gerçek bellek
okunmadı. Bu kayıt kimliği doğrulanmış otorite kanıtı değildir.

## Sonraki gözlem: altı ayrı hak

Farklı bir Extension Host/worker örneğinde altı sabit hak ayrı ayrı istendi:

| Hak | Gözlenen sonuç |
|---|---|
| DUP_HANDLE | DENIED — Windows hata 5 |
| VM_WRITE | DENIED — Windows hata 5 |
| VM_OPERATION | DENIED — Windows hata 5 |
| CREATE_THREAD | DENIED — Windows hata 5 |
| WRITE_DAC | DENIED — Windows hata 5 |
| WRITE_OWNER | DENIED — Windows hata 5 |

Ölçümün tamamlanması OBSERVED olarak kaydedildi. Bu deney bellek okumadı/yazmadı,
handle kopyalamadı, thread oluşturmadı veya izin değiştirmedi; yalnız istenen hakkın
verilip verilmediğini gözledi ve verilen handle'ları kullanmadan kapatacak şekilde tasarlandı.

## Birlikte nasıl yorumlanmalı?

Altı ret, korumalı çocuk süreç adayını değerlendirmeyi sürdürmek için olumlu ve dar
bir bulgudur. Yeni deney VM_READ istemedi; önceki deneyle aynı süreç örneği değildi.
Önceki FAIL düzeltilmiş sayılamaz. Thread/token, IPC, loader ve ağ için toplu kabul yoktur.

Durum: UNAUTHENTICATED_DIAGNOSTIC; host_acceptance NOT_ASSESSED.
Korunan doğrulayıcı ve gerçek otorite entegrasyonu tamamlanmamıştır.

## Dayanak kayıtları

Özel arşivdeki `155_host_worker_acl_analysis_2026-10-13`,
`157_host_access_matrix_2026-10-13` ve `158_host_parent_access_result_2026-10-13`.
Son çalıştırmanın dört executable/probe hash'i ve 25 incelenmiş kaynak hash'i yerel
karşılaştırmada eşleşmiştir. Ham izin ve süreç kimlikleri bu özete alınmamıştır.
