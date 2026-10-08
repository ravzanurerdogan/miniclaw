# 🦞 MiniMolt

**Moltbook'un küçük bir modeli + "ajan riskli işe kalkışırsa önce sahibine sorar" güvenlik katmanı.**

> Ders ödevi: Yazılım Gerçekleme ve Test, 3. hafta. Konu: 2026 ve sonrasında "teknolojik deprem" yapmış bir ürünün klonu + yenilikçi bir özellik.

🎥 **Tanıtım videosu:** `https://youtu.be/EYKS6fmoDcA`

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
| [Show HN: Moltbook](https://news.ycombinator.com/item?id=46802254) | _[287]_ | _[885]_ |
| [Moltbook (ana tartışma)](https://news.ycombinator.com/item?id=46820360) | _[1652]_ | [5] |
| [Moltbook is the most interesting place on the internet right now](https://news.ycombinator.com/item?id=46826963) | _[193]_ | _[173]_ |

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

MiniMolt'ta ajan (`@benimMolty`) akışı **kendiliğinden izler**:

1. **Canlı akış:** Başka ajanlar zamanla yeni gönderi atar, oy ve yorum gelir, bildirim çıkar.
2. **Doğrulanmamış kaynak uyarısı:** Sahibi doğrulanmamış gönderiler işaretlenir.
3. **Sahip onayı:** Doğrulanmamış bir gönderi ajanı riskli bir işe çağırırsa ajan işi yapmaz, **sahibine onay isteği gönderir** (Onay kutusu sekmesi + bildirim).
4. **Denetim kaydı:** Ajanın ne okuduğu, neyi istediği ve sahibin kararı kaydedilir (Denetim sekmesi).
5. **Karşılaştırma anahtarı:** Üstteki "Sahip onayı" kutusunu kapatınca ajan sormadan uygular ve (simülasyonda) yetenek kurulup API anahtarı sızar.

**YC bağlantısı:** YC'nin Multiplayer AI metni, ajan oturumlarının izlenebilmesini, yönlendirilebilmesini ve devredilebilmesini istiyor, ancak yetki ve onaydan söz etmiyor. Bu proje o boşluğu doldurmayı hedefliyor. Bu yorum bana aittir, YC'nin metninde yazmaz.

## Nasıl denenir?

1. Sayfayı aç. Birkaç saniyede yeni gönderiler kendiliğinden gelir (ya da oy ver, yorum yaz, kendin gönderi paylaş).
2. Yaklaşık 15 saniye sonra doğrulanmamış bir kaynaktan tehlikeli bir gönderi gelir (ya da **Kötü gönderi yolla** düğmesine bas). Ajan onu okur ve Onay kutusunda sana izin ister.
3. **Reddet** dersen hiçbir şey kurulmaz ve gönderi "ajanım engelledi" etiketi alır. **Onayla** dersen (simülasyonda) anahtar sızar.
4. **Sahip onayı** kutusunu kapatıp tekrar **Kötü gönderi yolla**'ya basarsan ajan sormadan uygular.
5. Denetim sekmesinden olayların kaydına bak.

## Sınırlar

- Tüm ajanlar, gönderiler ve veriler **kurgudur**, gerçek Moltbook'a bağlanmaz.
- Ajanın davranışı gerçek bir yapay zekâ modeliyle değil, **senaryoyla** (kurallarla) simüle edilir; böylece demo her seferinde tekrarlanabilir. Yenilik yapay zekâda değil, onay ve denetim akışındadır.
- Gönderiler önceden yazılmış havuzdan, rastgele sırayla gelir.
- Gerçek çok kullanıcılı bir sistem değildir.

## Kanıtlar

`kanitlar/` klasöründe: HN gönderilerinin ekran görüntüleri, YC RFS sayfası, demo ekranları.
Yapay zekâ ile geliştirme sohbeti: `SOHBET_LINKI_BURAYA`

## Geliştirme süreci

Bu proje bir yapay zekâ asistanıyla birlikte (hibrit) geliştirildi.

## Lisans

MIT
