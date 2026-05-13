# 🛡️ AltaySec Blue Team Interactive Labs - Memory Forensics (PoC)

Bu repository, siber güvenlik eğitim platformları için tasarlanmış, sıfır kurulum gerektiren (zero-setup), tarayıcı üzerinden çalışan ve CTF mantığıyla kodlanmış bir Blue Team / Olay Müdahale (Incident Response) bellek analizi (Memory Forensics) laboratuvar konseptidir.

### 🎯 Konsept: "Interactive Memory Detective"

Kullanıcılar, devasa boyutlardaki RAM imajlarını indirip sanal makine kurmakla uğraşmazlar. AltaySec'in özel geliştirdiği **Mock Volatility 3** simülatörü sayesinde, öğrenci doğrudan tarayıcı üzerinden bellek içi analiz, tehdit avcılığı ve zararlı yazılım tespiti yapar. Yeni nesil eğitim platformlarında olduğu gibi, analizciler bulgularını sistemdeki interaktif doğrulama scriptine girerek bayrağı (Flag) elde ederler.

### ✨ Öne Çıkan Özellikler:

* **Tarayıcı Tabanlı Özel Terminal:** `ttyd` aracı kullanılarak Docker içindeki bash terminali doğrudan web tarayıcısına yansıtılır. SSH bağlantısı gerektirmez.
* **Mock Volatility Simülatörü:** Gb'larca RAM imajı indirmeye gerek bırakmayan, Python ile kodlanmış ve gerçek Volatility 3 çıktıları üreten hafif bir simülatör altyapısı.
* **Anti-Cheat (Hile Koruması):** Bayrakları (Flag) veren bash scriptleri `shc` ile derlenerek okunamaz makine kodu (Binary) haline getirilmiştir. Analizci, analiz yapmadan bayrağa ulaşamaz.
* **Tam İzolasyon:** Her seviye kendi `docker-compose` ağı içinde yalıtılmış olarak çalışır.

### 🚀 Lab Nasıl Çalıştırılır?

Herhangi bir Docker yüklü sistemde, çözmek istediğiniz seviyenin klasörüne (Örn: `Altay_Sec_Memory_Easy`) girip şu komutları çalıştırmak yeterlidir:

1. Konteyneri inşa edin ve başlatın:
```bash
docker-compose up -d --build
```
* Tarayıcınızdan terminale erişin (İlgili port üzerinden, örn: http://localhost:8080).

* Analizi bitirdiğinizde terminale ./submit yazarak interaktif sınav sistemini başlatın!

---

## 🟢 Level 1: System Triage (Kolay)
**Odak Noktası:** Volatility 3 Temelleri, İşletim Sistemi Triyajı, Çalışan Süreçlerin (Processes) Analizi.

## 📝 Senaryo:
Şirket ağındaki bir bilgisayarda garip yavaşlamalar tespit edildi. Olay Müdahale (IR) ekibi fişi çekmeden önce makinenin RAM imajını (suspect.raw) aldı. İlk incelemeyi (`System Triage`) yapman ve şüpheli süreçleri tespit etmen bekleniyor.

## 🎯 Görevler:

`vol` aracını (`./vol -f suspect.raw plugin_adi`) kullanarak bellek imajını analiz et.

* İmajı alınan makinenin işletim sistemi versiyonunu (OS) bul (`windows.info`).

* Sistemde yetkisiz olarak çalışan şüpheli uygulamanın adını bul (`windows.pslist`).

* Bu şüpheli uygulamanın PID (`Process ID`) değerini tespit et.

* `./submit` çalıştır ve Flag'i kap.

---
