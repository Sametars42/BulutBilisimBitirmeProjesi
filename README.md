#  BulutBilisim_BitirmeProjesi            ( Başlama/Biriş Tarihi: 20.10.2026-(-) )
#  AWS Bulut Tabanlı Dağıtık Sunucu Yönetim ve Otomasyon Platformu

> Bulut Bilişim Operatörlüğü Bölümü Bitirme Projesi  
> Geliştirici: Samet Arslan  

### Proje Genel Bakışı ve Amacı
Bu proje; veri merkezleri, bulut altyapıları ve yerel ağlarda bulunan tüm fiziksel ve sanal sunucuların, Amazon Web Services (AWS) üzerinde barındırılan merkezi bir web yönetim paneli aracılığıyla uçtan uca izlenmesini, yönetilmesini ve güvenliğinin sağlanmasını amaçlayan bulut yerleşik kurumsal bir altyapı otomasyon platformudur. Günümüz çoklu sunucu barındıran mimarilerinde kaynak kullanımlarını ayrı ayrı takip etmenin ve servisleri farklı araçlarla yönetmenin yarattığı karmaşıklığı ortadan kaldırmak amacıyla geliştireceğim. Projem, Proxmox VE, Portainer, Datadog ve Zabbix gibi kurumsal izleme araçlarının sunduğu güçlü yetenekleri; C# tabanlı ajan mimarisi, REST API, MS SQL Server veritabanı ve AWS bulut altyapısı bileşenleriyle birleştirerek tek bir ekranda toplar.

### Sistem Mimarisi ve Çalışma Prensibi
Sistem, merkezi yönetim sunucusu ile yönetilen uç sunucular arasında kurulan güvenli bir haberleşme döngüsüne dayanır. Uzak fiziksel veya sanal sunucular üzerinde arka planda çalışan hafif C# Ajan (Agent) yazılımı, sistemin anlık kaynak tüketimlerini (CPU, RAM, Disk ve Ağ metriklerini) düzenli aralıklarla okuyarak AWS EC2 üzerinde koşan ASP.NET Core tabanlı merkezi API'ye HTTP POST istekleriyle aktarır. AWS tarafında karşılanan bu veriler doğrulanarak MS SQL Server veritabanındaki ilişkisel tablolarda saklanır. Sistem yöneticisi ise modern web arayüzü üzerinden sisteme bağlanarak tüm sunucuların sağlık durumunu canlı grafikler ve zaman serisi analizleriyle izleyebilir, gerektiğinde web tabanlı SSH bağlantısı kurarak veya API komutları göndererek sunuculara uzaktan müdahale edebilir.

### Kullanılan Teknolojiler ve Altyapı Bileşenleri
* Bulut Altyapısı: AWS EC2 (Ubuntu / Windows Server ortamları)
* Merkezi Web Arayüzü (Dashboard): HTML5, CSS3, JavaScript / Blazor / React
* Backend ve API Katmanı: C# ASP.NET Core Web API
* Ajan Yazılımı (Remote Agent): C# .NET Core Konsol / Arka Plan Servisi
* Veritabanı Yönetimi: MS SQL Server 
* Protokoller ve İletişim:  REST API (JSON), SSH, Canlı Veri Akışı için Websocket ve ICMP Ping

### Modüler Geliştirme Yol Haritası
* V1 — Server Management: AWS tabanlı web tabanlı envanter ve varlık yönetimi.
* V2 — Server Access & Management: Web SSH entegrasyonu ve uzaktan servis/süreç kontrolü.
* V3 — Monitoring & Alerting: Canlı izleme paneli, zaman serisi grafikleri ve eşik aşımlarında anlık uyarı mekanizmaları.
* V4 — Network & Security: Güvenlik duvarı (Firewall) kuralları, port ve IP engelleme otomasyonu.
* V5 — Docker & Virtualization: Konteyner yaşam döngüsü (başlat/durdur/log) ve sanal makine yönetim modülleri.
