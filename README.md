# Zywexx - Kişisel Portfolyo Sitesi

> Şık, modern ve tamamen özelleştirilebilir bir portfolyo / kartvizit web sitesi.  
> Tek ekranlık bir profil kartı: müzik çalar ve animasyonlu bir arayüz.

![GPL-3.0 License](https://img.shields.io/badge/License-GPLv3-blue.svg)

---

## 🚀 Özellikler

- ✨ **Giriş ekranı** ile kullanıcı deneyimi
- 🖼️ **Fullscreen arka plan resmi** (kendi görselinizi koyun)
- 🎵 **Müzik çalar** – otomatik başlar, tek parça döngü
- ⌨️ **Yazı efekti (typewriter)** – bio metniniz animasyonlu
- 🧩 **Rozetler** – istediğiniz görselleri ekleyin
- 🔗 **Sosyal medya bağlantıları** – renkli hover efekti
- 📱 **Tam duyarlı (responsive)** – mobil, tablet, masaüstü
- 🌙 **Glassmorphism & blur efekti** – şeffaf kart

---

## 📁 Dosya Yapısı

```
proje-kök/
├── index.html          # Ana dosya (tüm CSS/JS içinde)
├── arkaplan.png        # Arka plan resminiz (öneri: 1920x1080+)
├── profilResmi.jpg     # Profil fotoğrafınız (kare, öneri: 512x512)
├── kapakResmi.jpg      # Müzik çalar kapak resmi (kare, öneri: 512x512)
├── dosyaLinki.mp3      # Çalınacak müzik dosyası (MP3)
└── README.md           # Bu dosya
```

**Not:** Tüm özelleştirmeler `index.html` içindeki **`kullaniciAyarlari`** nesnesi üzerinden yapılır.  
Dosya isimlerini ve yollarını bu nesneye işleyin.

---

## ⚙️ Kurulum & Yapılandırma

### 1. Dosyaları hazırlayın
- `arkaplan.png` – sitenin arka planında görünecek (dosya adı sabit, değiştirmeyin)
- `profilResmi.jpg` – kartın solundaki profil resmi
- `kapakResmi.jpg` – müzik widget’ının solundaki küçük kapak
- `dosyaLinki.mp3` – arka planda çalacak müzik (isteğe bağlı, boş bırakırsanız çalmaz)

### 2. `index.html` içindeki ayarları düzenleyin

Aşağıdaki kod bloğunu `script` etiketleri içinde bulacaksınız.  
Tüm kişisel bilgilerinizi buraya girin.

```javascript
const kullaniciAyarlari = {
    isim: "Zywexx",                           // Kullanıcı adınız
    bioMetni: "787 INC. XD",                 // Bio yazısı (typewriter ile animasyonlu)
    profilResmi: "profilResmi.jpg",          // Profil fotoğrafı dosya yolu
    rozetler: [                              // Rozet görselleri (URL veya göreceli yol)
        "https://cdn3.emoji.gg/emojis/552821-xverified.png",
        "https://cdn3.emoji.gg/emojis/702380-developer.png",
    ],
    muzik: {
        dosyaLinki: "dosyaLinki.mp3",        // Müzik dosyası yolu
        sarkiAdi: "Aslan yakışmaz kafeste",  // Şarkı adı
        sanatci: "Keskin",                   // Sanatçı adı
        kapakResmi: "kapakResmi.jpg"         // Kapak resmi yolu
    },
    sosyalMedya: [                           // Sosyal medya bağlantıları
        { ikon: "fa-brands fa-discord", link: "https://discord.gg/CUFXct9PNz", renk: "#5865F2" },
        { ikon: "fa-brands fa-spotify", link: "https://open.spotify.com/user/...", renk: "#1DB954" },
        { ikon: "fa-brands fa-github", link: "https://github.com/Zywexx", renk: "#ffffff" },
        { ikon: "fa-solid fa-link", link: "https://guns.lol/Zywexx", renk: "#FFFFFF" }
    ]
};
```

#### 🔧 Açıklamalar

| Alan | Ne işe yarar |
|------|---------------|
| `isim` | Ana kartta büyük yazılan kullanıcı adı |
| `bioMetni` | Tip yazar efektiyle yazılacak metin |
| `profilResmi` | Karttaki profil resmi (göreceli veya mutlak yol) |
| `rozetler` | Dizi – her eleman bir resim URL’si. İsimlerin yanında gösterilir. |
| `muzik` | Müzik çalar ayarları. `dosyaLinki` boş olursa çalar görünmez. |
| `sosyalMedya` | Butonlar – `ikon` için [FontAwesome 6](https://fontawesome.com/v6/search) class’ları kullanılır.<br>`renk` hover’da butonun arka plan rengi olur. |

---

## 🎨 Arka Plan ve Görseller

- Arka plan resmi `arkaplan.png` olarak sabitlenmiştir.  
  - CSS’de `#bg-image` içinde `background-image: url('arkaplan.png');` ile tanımlıdır.  
  - İsterseniz başka bir formatta (jpg, webp) değiştirebilirsiniz, sadece dosya adını güncelleyin.

- Diğer tüm görsellerde **yedek mekanizma** vardır:  
  Belirtilen dosya bulunamazsa varsayılan bir placeholder resim gösterilir (konsola uyarı yazılır).

---

## 🎵 Müzik Çalar

- Müzik dosyası `dosyaLinki.mp3` olarak ayarlanmıştır.
- Sayfa giriş yapıldıktan sonra **otomatik başlar** (tarayıcı politikaları nedeniyle bazı ortamlarda çalışmayabilir – kullanıcı etkileşimi gerektiği için `Click to enter...` ekranı ile başlatılır).
- Müzik butonu ile oynat/duraklat yapılabilir, ayrıca sol üstteki **ses simgesi** ile sessize alınabilir.
- Albüm resmi döner animasyon yapar (çalarken).

> `.mp3` dosyası yerine herhangi bir ses dosyası kullanılabilir, sadece `dosyaLinki` uzantısını doğru girin.

---

## 🌐 Sosyal Medya Butonları

`kullaniciAyarlari.sosyalMedya` dizisinde her nesne için:

- `ikon` → FontAwesome sınıfı (örnek: `fa-brands fa-github`)
- `link` → Tıklanınca gidilecek URL (yeni sekmede açılır)
- `renk` → Fare üzerine gelince butonun arka plan rengi (istediğiniz hex veya rgb)

> Butonlara **varsayılan hover efekti** uygulanır: renk değişir ve gölgelenir.

---

## 🧩 Özelleştirme İpuçları

### Typewriter hızını değiştirme

`setupTypewriter()` fonksiyonunda `speed` değişkenlerini oynayın:
- Yazma hızı: `100` ms
- Silme hızı: `50` ms
- Bekleme süresi: `2000` ms

### Sparkle (parıltı) efektini kapatma veya hızlandırma

`initSparkles()` içindeki `setInterval` süresini (`100`) değiştirin veya fonksiyonu tamamen kaldırın (çağrıldığı satırı silin).

---

## 📄 Lisans

Bu proje **GNU General Public License v3.0** ile lisanslanmıştır.  
Bu, şu anlama gelir:

- ✅ **Kullanabilir, paylaşabilir, değiştirebilirsiniz**.
- ✅ **Ticari veya kişisel projelerde kullanabilirsiniz**.
- ❌ **Kapalı kaynak olarak dağıtamazsınız** – türev çalışmalar aynı lisansı kullanmalıdır.
- ❌ **Sorumluluk reddi** – yazılım “olduğu gibi” sunulur, hiçbir garanti yoktur.

Tam lisans metni için: [GNU GPLv3](https://www.gnu.org/licenses/gpl-3.0.txt)

---

## 🤝 Katkıda Bulunma

Projeyi geliştirmek isterseniz:

1. Bu depoyu forklayın.
2. Yeni bir dal oluşturun (`git checkout -b yeni-ozellik`)
3. Değişikliklerinizi yapın ve commit edin.
4. Push edin ve Pull Request açın.

Her türlü iyileştirme, hata düzeltmesi veya dökümantasyon güncellemesi memnuniyetle karşılanır.

---

## 🙏 Teşekkürler

- **FontAwesome** & **Google Fonts** – Simge ve tipografi

---

## 📬 İletişim

- Discord: [787 Projects](https://discord.gg/CUFXct9PNz)
- GitHub: [Zywexx](https://github.com/Zywexx)

---

**⭐ Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!**