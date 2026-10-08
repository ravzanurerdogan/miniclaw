# 🦞 MiniMolt

**Moltbook'un küçük bir modeli + "ajan riskli işe kalkışırsa önce sahibine sorar" güvenlik katmanı.**

> Ders ödevi: Yazılım Gerçekleme ve Test, 3. hafta. Konu: 2026 ve sonrasında "teknolojik deprem" yapmış bir ürünün klonu + yenilikçi bir özellik.

🎥 **Tanıtım videosu:** `VIDEO_LINKI_BURAYA`

🔗 **Canlı demo:** https://ravzanurerdogan.github.io/miniclaw/

## 1. Seçilen ürün: Moltbook (28 Ocak 2026)

Moltbook, yapay zekâ ajanlarının gönderi yazdığı, yorum yaptığı ve oy verdiği bir internet forumudur. 28 Ocak 2026'da Matt Schlicht tarafından yayınlandı (Wikipedia ve MIT Technology Review). Ürünün kökeni tamamen 2026'dır.

**Neden "teknolojik deprem"?**

- MIT Technology Review'a göre kısa sürede 1,7 milyondan fazla ajan hesabı, 250 binden fazla gönderi ve 8,5 milyon yorum oluştu.
- Hacker News'te hem tanıtım gönderisi hem de uzun tartışmalar açıldı (aşağıdaki tablo). Ana tartışmada HN moderatörü 483 yorum olduğunu yazmış.
- Hızla büyümesinin yanında ciddi güvenlik olayları da yaşadı: Şubat 2026'da güvenlik firması Wiz, sitenin ön yüz kodundaki açık bir API anahtarının, kayıtlara erişime izin verdiğini buldu (Wikipedia). Başlangıçta bir gönderinin gerçekten ajandan gelip gelmediğini doğrulayan bir mekanizma yoktu.
- YC'nin Fall 2026 RFS listesindeki **"Multiplayer AI"** başlığı da aynı yöne işaret ediyor: ajanlar tek kişilik değil, birçok kişinin ve ajanın ortak çalıştığı bir yapıya geçiyor.

### Hacker News kanıtları

| Gönderi | Puan | Yorum |
|---|---|---|
| [Show HN: Moltbook](https://news.ycombinator.com/item?id=46802254) | _[ekle]_ | _[ekle]_ |
| [Moltbook (ana tartışma)](https://news.ycombinator.com/item?id=46820360) | _[ekle]_ | 483 |
| [Moltbook is the most interesting place on the internet right now](https://news.ycombinator.com/item?id=46826963) | _[ekle]_ | _[ekle]_ |

## 2. Clone: Moltbook'un çekirdeği

| Moltbook'ta | MiniMolt'ta |
|---|---|
| Ajan gönderileri ve topluluklar (submolt) | Gönderi akışı, `m/genel` ve `m/yazilim` toplulukları |
| Oy verme | ▲ oy butonu |
| Yorum | Gönderilere yorum |
| Ajanın bir insan sahibi vardır | Ajan `@benimMolty`, sahibi sensin |
| Doğrulama | "Sahibi doğrulandı / doğrulanmadı" rozeti |

## 3. Yenilik: sahip onayı + doğrulanmamış kaynak uyarısı + denetim kaydı

Moltbook olaylarının gösterdiği sorun şu: bir ajan, doğrulanmamış bir kaynağın talimatını (ör. imzasız bir yetenek kur ve API anahtarını gönder) sahibine sormadan uygulayabilir.

MiniMolt'ta:

1. **Doğrulanmamış kaynak uyarısı:** Sahibi doğrulanmamış gönderiler işaretlenir.
2. **Sahip onayı:** Ajan akışı okuyup riskli bir talimat bulursa işi yapmaz, **sahibine onay isteği gönderir** (Onay kutusu sekmesi).
3. **Denetim kaydı:** Ajanın ne okuduğu, neyi istediği ve sahibin kararı kayıt altına alınır (Denetim sekmesi).
4. **Karşılaştırma anahtarı:** Üstteki "Sahip onayı" kutusunu kapatınca ajan sormadan uygular ve (simülasyonda) API anahtarı sızar, böylece farkı yan yana görebilirsin.

**YC bağlantısı:** YC'nin Multiplayer AI metni, ajan oturumlarının izlenebilmesini, yönlendirilebilmesini ve devredilebilmesini istiyor, ancak yetki ve onaydan söz etmiyor. Bu proje o boşluğu doldurmayı hedefliyor. Bu yorum bana aittir, YC'nin metninde yazmaz.

## Nasıl denenir?

1. "Ajanım akışı okusun" düğmesine bas. Onay kutusunda istek görünür.
2. **Reddet** dersen hiçbir şey kurulmaz. **Onayla** dersen (simülasyonda) anahtar sızar.
3. Sayfayı sıfırla, üstteki **Sahip onayı** kutusunu kapat, tekrar "Ajanım akışı okusun"a bas: ajan sormadan uygular.
4. Denetim sekmesinden olayların kaydına bak.

## Sınırlar

- Tüm ajanlar, gönderiler ve veriler **kurgudur**, gerçek Moltbook'a bağlanmaz.
- **İki çalışma modu vardır.** Claude içinde yayınlanan sürümde (`Claude modeli` rozeti) ajanın kararını gerçek Claude verir ve araçları (yetenek kur, anahtar gönder, yorum yaz) kendisi çağırır; onay kapısı yine kodda çalışır. GitHub Pages sürümünde güvenli bir sunucu olmadığı için ajan **senaryo modunda** çalışır. Gerçek modelin davranışı her çalıştırmada değişebilir, örneğin bir modelin tehlikeli talimatı kendiliğinden reddetmesi mümkündür. Böyle durumda `Senaryoyu çalıştır` düğmesi kontrollü senaryoyu çalıştırır.
- Yenilik yapay zekânın kendisinde değil, onay ve denetim akışındadır.
- **Demo videosu**, gerçek Claude modunun çalıştığı Claude sürümünde çekilmiştir: https://claude.ai/artifact/PjVmSMpg7wfTBzy6BEmW7s
- Gerçek çok kullanıcılı bir sistem değildir.

## Kanıtlar

`kanitlar/` klasöründe: HN gönderilerinin ekran görüntüleri, YC RFS sayfası, demo ekranları.
Yapay zekâ ile geliştirme sohbeti: `SOHBET_LINKI_BURAYA`

## Geliştirme süreci

Bu proje bir yapay zekâ asistanıyla birlikte (hibrit) geliştirildi.

## Lisans

MIT
