<div align="center">

# ◉ Kara Delik Simülasyonu

[English](README.md) · [Türkçe](README.tr.md)

**Tarayıcında, gerçek zamanlı genel görelilik ışın izleme.**

Dönen bir kara deliğin çevresinde ışığın nasıl büküldüğünü keşfet: kamerayı hareket ettir, fiziksel parametreleri değiştir ve olay ufkuna doğru düş.

`WebGL 2` · `Vanilla JavaScript` · `GLSL` · `Bağımlılık yok`

</div>

---

## Neler var?

| Görselleştirme | Etkileşim |
| :--- | :--- |
| Eğri uzay-zamanda piksel başına jeodezik ışın izleme | Sinematik, serbest kamera, otomatik tur ve serbest düşüş modları |
| Kütleçekimsel merceklenme, kara delik gölgesi ve foton halkası | Dönme, eğim, uzaklık, görüş açısı ve disk ayarları |
| Novikov–Thorne ince diski, Doppler etkisi ve kütleçekimsel kırmızıya kayma | Sekiz hazır sahne, kalite seçenekleri ve ekran görüntüsü alma |
| Kodla üretilen yıldızlar, Samanyolu ve isteğe bağlı göreli jet | Işık yolları diyagramı ve EHT görünümü benzetimi |

## Çalıştırma

Güncel bir **WebGL 2 destekli tarayıcı** kullan. Proje için kurulum veya paket yöneticisi gerekmiyor.

```bash
python -m http.server 8000
```

Ardından [http://localhost:8000](http://localhost:8000) adresini aç. `index.html` dosyasını doğrudan tarayıcıda açmak da mümkündür.

> GPU gücüne göre görüntü kalitesi ve kare hızı değişir. Sağdaki panelden ışın izleme kalitesini düşürebilirsin.

## Kontroller

| İşlem | Kontrol |
| :--- | :--- |
| Kamerayı döndür / etrafa bak | Sürükle / `Shift` + sürükle |
| Yaklaş veya uzaklaş | Fare tekerleği |
| Sinematik / serbest / düşüş | `C` / `O` / `D` |
| Hazır sahne seç | `1`–`8` |
| Otomatik tur / zamanı durdur | `T` / `Boşluk` |
| Arayüz / ayarlar / bilgi | `H` / `P` / `I` |
| Tam ekran / ekran görüntüsü | `F` / `S` |

## Nasıl çalışır?

Işık ışınları Hamilton denklemleriyle izlenir. CPU tarafındaki fizik çekirdeği `js/physics.js` içindedir; GLSL ışın izleyici ve görüntü işleme aşamaları `js/shaders.js` içindedir. `js/main.js` kamera, WebGL hattı ve arayüzü yönetir. Diskin sıcaklığı Novikov–Thorne modeline dayanır; yıldızlar ve disk dokusu dış görsel dosyalara ihtiyaç duymadan üretilir.

EHT görünümü, çözünürlüğü taklit eden **görsel bir benzetimdir**; gerçek teleskop verisi değildir.

## Doğrulama

Fizik çekirdeği analitik gölge, kritik yörünge, ISCO ve serbest düşüş sonuçlarına karşı sınanır:

```bash
node dev/test_physics.js
```

## Proje yapısı

```text
index.html           Arayüz ve giriş noktası
js/physics.js        Kara delik fiziği ve jeodezik hesapları
js/shaders.js        GLSL ışın izleme ve görüntüleme
js/main.js           Kamera, WebGL hattı ve etkileşim
dev/                 Fizik testleri ve geliştirme araçları
```
