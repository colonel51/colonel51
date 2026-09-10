### Merhaba, ben Ramazan 👋

**Backend & Full-Stack Developer.** Python/Django ile production sistemler geliştiriyor ve mimariden deploy'a kadar tek başıma işletiyorum.

`🏢 Multi-branch/multi-tenant` `⚡ Gerçek zamanlı (WebSocket)` `⚙️ Asenkron (Celery/Redis)` `🗄️ Veritabanı performansı` `🐳 Docker/Linux`

Şu anda **Near East Technology**'de dört eşzamanlı production sisteminden tek başıma sorumluyum; bunun yanında kendi kişisel/freelance projelerimi yürütüyorum. GitHub profilim çoğunlukla **private repo** içerdiği için dışarıdan boş görünüyor — aşağıda ne üzerinde çalıştığımın özeti var.

<br>

## 🛠️ Teknolojiler

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![DRF](https://img.shields.io/badge/Django%20REST-ff1709?style=for-the-badge&logo=django&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![React](https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

<br>

## 🌟 Bayrak Projeler

### Restoran Yönetim Sistemi

Çoklu şubeli bir restoran zincirinin sipariş akışını uçtan uca yönetmek için tasarladığım, canlı ortamda kullanılan bir platform. Web, kiosk ve call-center kanallarından gelen siparişleri tek bir gerçek zamanlı akışta birleştirip **7 farklı kullanıcı rolüne** role özel, anlık bilgi akışı sağlıyorum.

`Django · Channels · Celery · Redis · MySQL · React · TypeScript · Docker`

<details>
<summary>Detaylar</summary>
<br>

- 🔴 **Senkronizasyon:** Sipariş oluşturulduğu andan teslim edilene kadar her durum değişikliğini (hazırlanıyor → hazır → yolda → teslim edildi) WebSocket üzerinden ilgili role anında yayınlıyorum — sayfa yenilemeye gerek kalmadan mutfak, kurye ve müşteri ekranları senkron kalıyor.
- 🏗️ **Mimari:** Domain / Application / Infrastructure / Interface olarak katmanlı (Clean) bir mimari kurdum; iş kurallarını (services) veri erişiminden (repository implementasyonları) tamamen izole ettim.
- 🔁 **Şubeler arası operasyon:** Sipariş transferini şubeler arası birinci sınıf bir iş akışı olarak modelledim; yoğunluk/kapasite durumunda sipariş başka bir şubeye anlık devredilebiliyor.
- 🔐 **İleriye dönük güvenlik:** Kritik operasyonlar için ayrı bir denetim (audit) günlüğü, XSS koruması ve otomatik secret rotation altyapısı kurdum.
- ⚙️ **Asenkron işleyiş:** Bildirim gibi kullanıcıyı bekletmemesi gereken işleri Celery ile arka planda çalıştırıyorum; Redis'i hem cache hem WebSocket mesajlaşma katmanı olarak kullanıyorum.

</details>

<br>

### Ramot — Algoritmik Trading Platformu

Her kullanıcının kendi borsa hesabını bağladığı, Binance (kripto) ve XAUUSDT (altın) üzerinde otomatik trading botları çalıştırdığım multi-tenant bir platform. Sinyal güven skorlaması için Anthropic API'yi entegre ederek risk/kaldıraç kararlarını veriye dayalı hale getirdim.

`Django REST + Channels · Celery · Redis · PostgreSQL · React · TypeScript · Anthropic API`

<details>
<summary>Detaylar</summary>
<br>

- 🤖 **İki bağımsız bot:** CryptoBot 60 saniyede, GoldBot 5 dakikada bir kendi döngüsünde çalışıyor; Celery beat ile ayrı ayrı zamanlanıyor.
- 🧠 **AI destekli sinyal skorlama:** RSI/MACD/Bollinger/ATR tabanlı sinyalleri Anthropic API ile güven skoruna çeviriyorum; bu skor doğrudan pozisyon büyüklüğü/kaldıraç kararını besliyor.
- 🛡️ **Otomatik risk yönetimi:** Trailing stop, likidasyon koruması, günlük zarar ve maksimum drawdown limitleri; altın botunda ayrıca seans (Londra/NY/Asya) ve ADX filtreleri.
- 🔴 **Gerçek zamanlı dashboard:** Django Channels üzerinden canlı pozisyon ve fiyat akışını React arayüzüne WebSocket ile taşıyorum.
- 🔐 **Kullanıcı bazlı güvenlik:** Her kullanıcının borsa API anahtarları veritabanında şifreli tutuluyor; JWT + 2FA ile korunuyor.
- ✅ Birden fazla bağımsız hesapta canlı trading ile uçtan uca doğruladım, kapsamlı backtesting ile destekledim.

</details>

<br>

## 🔒 Diğer Projeler

Bunların dışında üzerinde çalıştığım/çalıştığım 9 private repo'dan öne çıkanlar:

| Proje | Açıklama | Teknolojiler | Durum |
|---|---|---|---|
| **El İşi Üreticileri için Multi-Tenant ERP** | Küçük ölçekli el işi üreticileri için malzeme, ürün, satış ve görev yönetimi sağlayan bir SaaS geliştirdim. Clean Architecture ile katmanlı bir mimari kurdum, JWT auth ve tenant izolasyonu ekledim. | Django REST Framework · React · JWT | 🟢 Aktif |
| **SaaS Starter Kit** | Multi-tenant SaaS ürünlerinde tekrar kullanmak üzere bir Django + React/TS başlangıç altyapısı (auth, Docker, temel proje iskeleti) geliştirdim. | Django · React (TS) · Docker | 🟡 Bakımda |
| **Kurumsal Web Sitesi — Oto Lastik Sektörü** | Bir oto lastik firması için kurumsal tanıtım ve yönetim paneli içeren bir web sitesi geliştirdim. | Django · React (TS) | ✅ Teslim edildi |
| **Kurumsal Web Sitesi — Metal Sektörü** | Bir metal sektörü firması için Django tabanlı bir kurumsal web sitesi geliştirdim. | Django · HTML/CSS · JavaScript | ✅ Teslim edildi |
| **Kişisel Portfolyo** | Kendi Django tabanlı portfolyo sitemi Nginx + systemd servisiyle production'a aldım. | Django · Nginx · Shell | 🟢 Aktif |
| **100 Days of Python** | Python temellerimi pekiştirmek için hazırladığım Jupyter Notebook tabanlı alıştırma/çalışma defterlerim. | Python · Jupyter Notebook | 📚 Öğrenme |
| **Python Alıştırmaları** | Temel Python pratik scriptlerim (koşullar, döngüler, mantıksal operatörler, küçük uygulamalar). | Python | 📚 Öğrenme |

<br>

## 📫 İletişim

📧 rkarsanba0@gmail.com
