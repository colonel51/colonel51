### Merhaba, ben Ramazan 👋

**Backend & Full-Stack Developer.** Çoklu şube ve çoklu kiracılı (multi-tenant) yapılarda gerçek kullanıcı trafiği taşıyan production sistemleri mimariden deploy'a kadar tek başıma sahipleniyorum.

Odak alanlarım: API tasarımı ve veritabanı performansı (composite index'ler, N+1 sorgu eliminasyonu), gerçek zamanlı iletişim (WebSocket tabanlı sipariş/bildirim akışları), asenkron görev işleme ve zamanlama, çok-kiracılı/clean architecture, production güvenliği (rate limiting, HTTPS/CORS, ortam bazlı gizli anahtar yönetimi). Bunları Python/Django ekosisteminde, React/TypeScript frontend'leriyle birlikte hayata geçiriyorum.

Şu anda **Near East Technology**'de dört eşzamanlı production sisteminin (restoran yönetimi, spor & havuz erişim kontrolü, okul yönetimi) mimarisi, geliştirmesi ve deploy'undan tek başıma sorumluyum. Bunların yanında kendi kişisel/freelance projelerimi de yürütüyorum.

GitHub profilim çoğunlukla **private repo** içerdiği için dışarıdan boş görünüyor — aslında öyle değil. Aşağıda üzerinde çalıştığım projelerin kısa bir özeti var.

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

## 🌟 Bayrak Proje: Restoran Yönetim Sistemi

Çoklu şubeli bir restoran zincirinin sipariş akışını uçtan uca yönetmek için tasarladığım, canlı ortamda kullanılan bir platform. Web, kiosk ve call-center kanallarından gelen siparişleri tek bir gerçek zamanlı akışta birleştirip **7 farklı kullanıcı rolüne** (Admin, Call Center, Şube Müdürü, Aşçı, Kurye, Kasiyer, Müşteri) role özel, anlık bilgi akışı sağlıyorum.

- 🔴 **Senkronizasyon:** Sipariş oluşturulduğu andan teslim edilene kadar her durum değişikliğini (hazırlanıyor → hazır → yolda → teslim edildi) WebSocket üzerinden ilgili role anında yayınlıyorum — sayfa yenilemeye gerek kalmadan mutfak, kurye ve müşteri ekranları senkron kalıyor.
- 🏗️ **Mimari:** Domain / Application / Infrastructure / Interface olarak katmanlı (Clean) bir mimari kurdum; iş kurallarını (services) veri erişiminden (repository implementasyonları) tamamen izole ettim — bu da test edilebilirliği ve altyapı değişikliklerine karşı dayanıklılığı artırıyor.
- 🔁 **Şubeler arası operasyon:** Sipariş transferini şubeler arası birinci sınıf bir iş akışı olarak modelledim; yoğunluk/kapasite durumunda sipariş başka bir şubeye anlık devredilebiliyor.
- 🔐 **İleriye dönük güvenlik:** Kritik operasyonlar için ayrı bir denetim (audit) günlüğü, XSS koruması ve otomatik secret rotation altyapısı kurdum — güvenliği sonradan eklenen değil, sistemin bir parçası olarak tasarladım.
- ⚙️ **Asenkron işleyiş:** Bildirim gibi kullanıcıyı bekletmemesi gereken işleri Celery ile arka planda çalıştırıyorum; Redis'i hem cache hem WebSocket mesajlaşma katmanı olarak kullanıyorum.

`Django · DRF · Channels · Celery · Redis · MySQL · React · TypeScript · Docker · Nginx`

<br>

## 🔒 Diğer Private Projeler

| Proje | Açıklama | Teknolojiler | Durum |
|---|---|---|---|
| **Ramot — Algoritmik Trading Platformu** | Binance (kripto) ve XAUUSDT (altın) için otomatik trading botları çalıştıran multi-tenant bir SaaS geliştirdim. RSI/MACD/Bollinger/ATR tabanlı sinyal motorları yazdım, otomatik risk yönetimi (trailing stop, likidasyon koruması, drawdown limitleri) kurdum, sinyal güven skorlaması için Anthropic API'yi entegre ettim ve gerçek zamanlı bir React dashboard geliştirdim. Birden fazla bağımsız hesapta canlı trading ile uçtan uca doğruladım. | Django REST + Channels · Celery · Redis · PostgreSQL · React (TS) · Anthropic API | 🟢 Aktif |
| **El İşi Üreticileri için Multi-Tenant ERP** | Küçük ölçekli el işi üreticileri için malzeme, ürün, satış ve görev yönetimi sağlayan bir SaaS geliştirdim. Clean Architecture ile katmanlı bir mimari kurdum, JWT auth ve tenant izolasyonu ekledim. | Django REST Framework · React · JWT | 🟢 Aktif |
| **SaaS Starter Kit** | Multi-tenant SaaS ürünlerinde tekrar kullanmak üzere bir Django + React/TS başlangıç altyapısı (auth, Docker, temel proje iskeleti) geliştirdim. | Django · React (TS) · Docker | 🟡 Bakımda |
| **Kurumsal Web Sitesi — Oto Lastik Sektörü** | Bir oto lastik firması için kurumsal tanıtım ve yönetim paneli içeren bir web sitesi geliştirdim. | Django · React (TS) | ✅ Teslim edildi |
| **Kurumsal Web Sitesi — Metal Sektörü** | Bir metal sektörü firması için Django tabanlı bir kurumsal web sitesi geliştirdim. | Django · HTML/CSS · JavaScript | ✅ Teslim edildi |
| **Kişisel Portfolyo** | Kendi Django tabanlı portfolyo sitemi Nginx + systemd servisiyle production'a aldım. | Django · Nginx · Shell | 🟢 Aktif |
| **100 Days of Python** | Python temellerimi pekiştirmek için hazırladığım Jupyter Notebook tabanlı alıştırma/çalışma defterlerim. | Python · Jupyter Notebook | 📚 Öğrenme |
| **Python Alıştırmaları** | Temel Python pratik scriptlerim (koşullar, döngüler, mantıksal operatörler, küçük uygulamalar). | Python | 📚 Öğrenme |

<br>

## 📊 Genel Bakış

- 🔒 **9** aktif private proje (üzerine çalışılan tarih aralığı: 09.2025 – 09.2026)
- **Backend:** Python · Django · Django REST Framework · REST API Design · JWT · 2FA · Role-Based Access Control
- **Real-Time & Async:** Django Channels · WebSockets · Celery · Redis (Cache / Pub-Sub / Broker)
- **Veritabanı:** PostgreSQL · MySQL · Şema Tasarımı · Query Optimization (N+1 elimination)
- **Mimari:** Clean Architecture (Repository & DTO) · Multi-Tenant Architecture · Layered Architecture
- **Altyapı:** Docker · Docker Compose · Nginx · Linux · Git/GitHub
- **Frontend:** React · TypeScript · Redux Toolkit · Zustand · TanStack Query · Vite · TailwindCSS

<br>

## 📫 İletişim

📧 rkarsanba0@gmail.com
