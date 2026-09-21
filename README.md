# Anıl Karahan

Magnes bünyesinde teknik operasyon ve yazılım departmanı yöneticisiyim. Odak noktası, farklı markaların e-ticaret operasyonlarını ayakta tutan entegrasyon, veri senkronizasyonu, veritabanı altyapısı ve raporlama sistemleri.

## Teknoloji

- **Backend:** C#, .NET (Framework ve .NET 8+), ASP.NET Web API, Entity Framework (EF6 ve EF Core), Blazor Server
- **Veritabanı:** SQL Server 2022 Enterprise, Always On Availability Groups, WSFC, T-SQL, performans tuning
- **Frontend:** React, TypeScript, Vite, Tailwind, shadcn/ui, Angular, Blazor
- **Mobil:** Flutter, React Native
- **Raporlama:** Power BI, özel rapor motorları
- **Entegrasyon:** Netsis, Dynamics 365 F&O, kargo firmaları, MCP (Model Context Protocol)
- **Altyapı:** Windows Server, IIS, VMware, Docker

## SQL Server ve Always On

Veritabanı en güçlü olduğum alan. Kurumsal ölçekte, iki node'lu bir Always On mimarisi (Windows Server Failover Clustering, dosya paylaşımlı quorum, birden fazla availability group) uçtan uca bu çatı altında yönetiliyor. TB seviyesindeki veritabanları için paralel ve sıkıştırılmış bir yedekleme mimarisi, ve zamanlama çakışmalarından arındırılmış bir iş planı var.

Düzenli olarak karşılaşılan üç konu: production'da yüksek okuma yüküne sebep olan raporlama sorgularının optimizasyonu, yoğun eşzamanlılıkta ortaya çıkan kilitlenme (deadlock) sorunlarının çözümü, ve büyük tablolarda sistemi kilitlemeden yapılan toplu veri işlemleri. İki sistem arasındaki veri tutarsızlıklarını bulup gideren analiz ve göç (migration) çalışmaları da bunun bir parçası.

## Marka entegrasyonları (pazaryeri ve ERP)

Çok sayıda marka için pazaryeri/ERP veri akışı sürdürülüyor. Her marka için genelde birkaç bileşen bir arada: sipariş, stok, fiyat ve iade verisinin iki yönlü aktığı bir entegrasyon servisi, markanın kendi ekibinin eriştiği bir raporlama/müşteri paneli tarafı, ve bazı markalarda kargo irsaliyesi transferini otomatikleştiren bağımsız bir servis.

- **Watsons** — pazaryeri ile veri ambarı arasındaki tutarsızlıkları bulup gideren analiz çalışması; mobil/Click & Collect tarafında geliştirme.
- **KIKO** — sipariş/stok entegrasyonu ve irsaliye transferi.
- **L'Occitane** — fulfillment stok senkronizasyon mimarisi (senkronizasyon gecikmesi, sistemler arası tutarsızlık), sevkiyat durumu mantığı, iptal sipariş yönetimi, irsaliye entegrasyonu.
- **Rossmann** — entegrasyon ve raporlama; bir production kesintisinin kök neden analizi ve kalıcı çözümü.
- **Beymen** — entegrasyon servisi.
- **Arkopharma** — stok besleme entegrasyonu, irsaliye transferi, müşteri paneli/raporlama API'si.
- **Mustela** — müşteri paneli/raporlama API'si.
- **LCW** — entegrasyon servisi.
- **L'Oréal** — özel bir raporlama servisi.
- **Save The Duck** — stok besleme entegrasyonu.
- **Eyüp Sabri Tuncer** — entegrasyon ve müşteri paneli, erken aşamadan itibaren.
- **Varta/PMAktif** — sıfırdan bir entegrasyon servisi: dosya iletişimi, veritabanı katmanı, kargo durumu senkronizasyonu, zamanlanmış görevler.
- **Kiwi** — karşı tarafla birlikte iki yönde çalışan karşılıklı bir entegrasyon çifti.
- **Lider / Canias ERP** — Canias tarafıyla entegrasyon.
- **Saçhane** — entegrasyon ve müşteri paneli.
- **Wella** — kaynak sistemden hedef sisteme düzenli otomatik veri aktarımı.
- **Doğuş HRG** — bir veri kesintisinin kök neden analizi ve tekrarını önleyen izleme/uyarı mekanizması.
- **HepsiBurada, N11, Pazarama** — her biri için ayrı entegrasyon servisleri.
- **Sentos ERP** — entegrasyon servisi.
- Dynamics 365 Finance & Operations veri erişimi ve toplu kayıt gönderimi yapan bir uygulamanın teknik tasarımı — birçok marka entegrasyonunun ortak kullandığı ERP altyapısının bir parçası.

## Fulfillment, depo ve operasyon

Sipariş toplama, paketleme, kargo etiketi üretimi, sevkiyat durumu takibi ve iade süreçlerini kapsayan uygulama grubu. Depo ekibinin elle Excel'de yürüttüğü stok sayımı, depolar arası transfer ve iade kayıtları artık uygulamalar üzerinden işleniyor.

Ayrı bir depo operasyon uygulaması sayım ve sipariş planlama süreçlerini yönetiyor, kargo firmasıyla doğrudan konuşuyor ve etiket üretimini otomatikleştiriyor. Bir sonraki nesil, mobil tarafta da aynı operasyonu destekleyen bir uygulama içeriyor. Daha eski bir masaüstü projede, aynı işlevleri (sayım aktarımı, sipariş planlama) gören bir depo yönetim uygulaması vardı.

Analiz tarafında: bir depoda fiziksel sayımla sistem stoğu arasında yüz binlerce birim seviyesinde fark çıktığında, yanlış eşleşmiş ürün çiftlerinin tespiti; paket karmaşıklığına göre adil bir personel performans ölçümü; günlük depo/stok raporlarındaki sistemik veri hatalarının bu tür analizlerle yakalanması.

## Kargo ve etiketleme

Kargo firmasıyla konuşan ve sevkiyat durumunu senkronize eden entegrasyon; farklı markaların irsaliye bilgilerini kargo firmasına aktaran ayrı servisler; etiket üretimi için kullanılan format dönüştürme katmanı.

## ERP, CRM ve veri aktarımı

- Genel bir müşteri ilişkileri (CRM) paneli.
- ERP'ye toplu veri aktarımı yapan, form tabanlı bir uygulama.
- Ürün tanım/konfigürasyon verisini yöneten bir ürün konfigüratör uygulaması.
- Tedarikçi/marka tarafına açılan bir tedarik portalı.
- Personel bordro takibi için ayrı bir arayüz ve API.

## Satış ve raporlama sistemleri

Haftalık satış/stok raporlarını ve son kullanma tarihi kontrolünü tek bir otomatik panelde toplayan bir sistem. Dış veri kaynaklarına (satış, stok, ziyaret verisi) bağlanıp düzenli aralıklarla güncelleniyor, markalara zamanlanmış raporlar otomatik gönderiliyor; gönderim öncesi bir veri bütünlüğü kontrolünden geçiyor, böylece hatalı veri içeren bir rapor müşteriye gitmiyor.

İçerdiği bazı modüller: son kullanma tarihi takibi, satış özeti ve trend analizi, satış hedefi takibi, stok tükenme tahmini, negatif stok uyarısı, kargo faturası kontrolü, teslimat takip, iş takibi ve sistem sağlığı ekranları.

Ayrı bir uygulama, Trendyol üzerinden gelen müşteri sorularını tek bir panelden yönetip cevaplamayı sağlıyor — çoklu mağaza desteği ve cevap geçmişiyle. Bunların dışında, bir uyarı yönetim paneli ve genel amaçlı bir raporlama API/uygulaması da bu grupta.

## POS

Bir mağaza içi POS uygulamasının eski mimariden modern bir web teknolojisi yığınına taşınma süreci sürüyor. Mobil ve web tabanlı versiyonları da mevcut.

## Yapay zekâ destekli araçlar

SQL Server'a yapay zeka asistanlarının erişebilmesini sağlayan bir araç. Ayrıca, veri gizliliğinin öncelikli olduğu bir kurum içi kullanım senaryosu için self-hosted / on-premise LLM altyapısı planı.

## İç araçlar, izleme ve otomasyon

- Production'da yaşanan servis kesintilerinin kök neden analizi ve kalıcı çözümü (arka planda çöken servisler, bellek/kaynak yönetimi sorunları).
- Entegrasyon süreçlerinin çalışıp çalışmadığını otomatik izleyen ve bir süreç durduğunda uyaran bir izleme servisi.
- Şifre sıfırlama gibi tekrarlayan yönetim işlerini otomatikleştiren küçük iç uygulamalar.
- Belge/veri paylaşımı için bir iç portal.
- Satın alma sürecini takip eden bir uygulama.
- Bildirim/entegrasyon amaçlı bir mesajlaşma servisi.
- Hızlı prototipleme yaklaşımıyla kurulmuş, katmanlı mimariye (Onion Architecture) sahip bir backend MVP'si.

## Ekip ve süreç yönetimi

Beş kişilik teknik ekipte süreç sahipliği matrisi — POS, ERP, depo, test, raporlama, entegrasyon, fulfillment ve yeni geliştirme gibi alanlarda net sorumluluk dağılımı.
