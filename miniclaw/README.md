# 🦞 MiniClaw

**OpenClaw'ın küçük, onay mekanizmalı bir modeli.** Mesajla komut verirsin, ajan doğru yeteneği (skill) seçip çalıştırır. Geri alınamaz işlerde (e-posta gönderme, dosya silme) önce senden **onay ister**.

> Ders ödevi: Yazılım Gerçekleme ve Test, 3. hafta. Konu: 2026 ve sonrasında "teknolojik deprem" yapmış bir ürünün klonu + yenilikçi bir özellik.

🎥 **Tanıtım videosu:** `VIDEO_LINKI_BURAYA` (YouTube / Google Drive)

🔗 **Canlı demo:** `https://KULLANICI_ADIN.github.io/miniclaw/` (GitHub Pages'i açınca burası çalışır)

## 1. Seçilen ürün: OpenClaw

OpenClaw, mesajlaşma uygulamaları üzerinden komut verilen, açık kaynaklı kişisel bir yapay zekâ asistanıdır. Sen "bu maili at, şu dosyayı sil, takvime bak" dersin, ajan işi kendi seçtiği araçlarla yapar.

**Neden "teknolojik deprem"?**

- Proje Kasım 2025'te başladı, adı **30 Ocak 2026'da OpenClaw** oldu ve 2026'da küresel olarak patladı. Mart 2026 itibarıyla GitHub'da yaklaşık 247 bin yıldıza ulaştı (kaynak: Wikipedia, kendin teyit et).
- **OpenClaw 2.0**, 30 Ağustos 2026'da yayınlandı.
- Hacker News'te çok sayıda gönderiye ve uzun tartışmalara konu oldu (aşağıdaki linkler).
- YC'nin **Fall 2026 RFS** listesindeki **"Multiplayer AI"** başlığı ile aynı yöne işaret ediyor.

**Dürüstlük notu:** Proje teknik olarak 2025 sonunda doğdu; bilinen hâli, viral patlaması ve 2.0 sürümü 2026'dadır.

### Hacker News kanıtları

| Gönderi | Puan | Yorum |
|---|---|---|
| [OpenClaw surpasses React to become the most-starred…](https://news.ycombinator.com/item?id=47219250) | _[ekle]_ | _[ekle]_ |
| [OpenClaw is changing my life](https://news.ycombinator.com/item?id=46931805) | _[ekle]_ | _[ekle]_ |
| [OpenClaw (ClawdBot) joins OpenAI](https://news.ycombinator.com/item?id=47027907) | _[ekle]_ | _[ekle]_ |
| [OpenClaw is a security nightmare dressed up as a daydream](https://news.ycombinator.com/item?id=47479962) | _[ekle]_ | _[ekle]_ |
| [OpenClaw is dangerous](https://news.ycombinator.com/item?id=47064470) | _[ekle]_ | _[ekle]_ |

## 2. Clone: OpenClaw'ın çekirdeği

| OpenClaw'da | MiniClaw'da |
|---|---|
| Mesajla komut | Sohbet ekranı |
| Ajanın araç seçmesi | `plan` (kural modu) veya gerçek Claude modeli (araç çağırma) |
| Yetenekler (skills) | `skills` nesnesi: takvim, e-posta, dosya, hava, hafıza, hatırlatıcı |
| Hafıza dosyaları (SOUL / MEMORIES) | Hafıza sekmesi |
| Şeffaflık | Etkinlik sekmesindeki ajan günlüğü |

## 3. Yenilik: Onay mekanizması (human-in-the-loop)

HN tartışmalarında en çok dile getirilen sorun **güvenlik**: ajanlar özel verilere ve araçlara erişiyor. Bir yorumcu, önemli işlerin insan onayına bağlandığı kısıtlı bir ajanın daha güvenli olacağını söylüyor.

MiniClaw'da `risky` işaretli yetenekler çalışmadan önce **Onayla / Reddet** sorar. Sağ üstteki **"Onay modu"** kutusunu kapatınca orijinal OpenClaw gibi sormadan çalışır, böylece iki davranış yan yana karşılaştırılabilir.

## Nasıl çalıştırılır?

Kurulum yok. `index.html` dosyasını tarayıcıda aç.

## Sınırlar

- Veriler (mail, takvim, dosya, hava) **uydurma örnek veridir**, gerçek hesaplara bağlanmaz.
- Gerçek Claude modu sadece Claude arayüzünde barındırıldığında çalışır. GitHub Pages'te **kural modu** devreye girer (anahtar kelimelerle komut anlar).
- OpenClaw'ın WhatsApp/Telegram bağlantısı, çoklu kanal ve gerçek yetenek mağazası yoktur.

## Geliştirme süreci

Bu proje bir yapay zekâ asistanıyla birlikte (hibrit) geliştirildi.

## Lisans

MIT


## Kanıtlar

Çalışmanın gerçekten yapıldığını gösteren materyaller `kanitlar/` klasöründedir:

- `hn-*.png`: Hacker News gönderilerinin puan ve yorum sayısını gösteren ekran görüntüleri
- `yc-rfs.png`: YC Fall 2026 RFS sayfasının ekran görüntüsü
- `demo-onay.png`: Onay kartının çıktığı ekran
- `demo-onaysiz.png`: Onay modu kapalıyken dosyanın sormadan silindiği ekran
- Yapay zekâ ile geliştirme sohbetinin bağlantısı: `SOHBET_LINKI_BURAYA`

## Dosyalar

| Dosya | Açıklama |
|---|---|
| `index.html` | Uygulamanın tamamı (arayüz, yetenekler, planlayıcı, onay mekanizması) |
| `README.md` | Bu belge (ürün sunumu) |
| `kanitlar/` | Ekran görüntüleri |
