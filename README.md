# 🚀 NovaMart — Yapay Zeka Destekli Akıllı İade ve Şikayet Otomasyonu (İş Analizi Vaka Çalışması & BRD)

> **Rol:** İş Analisti (Business Analyst) Stajyer | **Hazırlayan:** Beyza Pamuk  
> **Metodoloji:** IIBA BABOK®, Agile Scrum, BPMN 2.0, Gherkin (BDD)  
> **Odak Alanları:** Süreç Modelleme (As-Is / To-Be), İş Gereksinimleri Belgesi (BRD), Yapay Zeka Karar Motoru Tasarımı, Uç Durum (Edge Case) Analizi, Ekipler Arası API Veri Sözleşmesi

## 📌 Proje Özeti (Executive Summary)

**NovaMart**, son 1 yılda sipariş hacmi **%60 büyüyen** orta-büyük ölçekli bir e-ticaret platformudur. Büyümeye rağmen kusurlu ve yanlış ürün iade süreçlerinin çağrı merkezi, e-posta ve departmanlar arası Excel tabloları üzerinden manuel yürütülmesi ciddi bir operasyonel darboğaz yaratmıştır.

Bu portfolyo projesinde; manuel iade operasyonlarını **Görüntü İşleme (Computer Vision)** ve **Doğal Dil İşleme (NLP)** destekli akıllı bir karar destek sistemine dönüştürmek için uçtan uca **İş Analizi (Business Analysis)** çalışması yürütülmüştür.

### 🎯 Problem ve Hedeflenen İş Değeri (SMART KPI'lar)

| Performans Göstergesi (KPI) | Mevcut Durum (As-Is) | Hedeflenen Durum (To-Be) | İş Etkisi / Zaman Sınırı |
| :--- | :--- | :--- | :--- |
| **Ortalama Çözüm Süresi** | 4 – 5 İş Günü | **< 1 Dakika** (Karmaşıkta Maks. 24 Saat) | İlk 3 Ay İçinde |
| **Müşteri Memnuniyeti (CSAT)** | %64 (%82'den geriledi) | **%85 ve Üzeri** | İlk 6 Ay İçinde |
| **Sahte İade (Fraud) Zararı** | Aylık ~450.000 TL Kayıp | **En Az %70 Azalma (~315.000 TL/Ay Tasarruf)** | İlk 6 Ay İçinde |
| **Zero-Touch Otomasyon Oranı** | %0 (Tamamen Manuel) | **%65+ Otomatik Sonuçlanma** | Canlıya Geçiş Sonrası |

## 📂 Depo (Repository) İçeriği ve Teslimatlar

* 📄 **`NovaMart_Is_Analizi_Vaka_Calismasi_ve_BRD.pdf`** — Paydaş analizi, kapsam, BPMN süreç şeması, fonksiyonel/fonksiyonel olmayan gereksinimler, kullanıcı hikayeleri ve API veri sözleşmesini içeren tam kapsamlı kurumsal PDF dokümanı.
* 📝 **`NovaMart_Is_Analizi_Vaka_Calismasi_ve_BRD.docx`** — Dokümanın Microsoft Word formatındaki düzenlenebilir versiyonu.
* 💻 **`NovaMart_BPMN_ve_Jira_Simulasyonu.html`** — Tek dosyada çalışan etkileşimli **As-Is / To-Be BPMN Süreç Haritası**, **Jira Scrum Panosu** ve **Canlı AI İade Karar Simülatörü** web uygulaması.

## 🔄 Mevcut (As-Is) ve Gelecek (To-Be) Süreç Mimarisi

* **Mevcut Süreç (As-Is):** Müşteri çağrı merkezini arar veya e-posta gönderir $\rightarrow$ Müşteri temsilcisi talepleri tek tek açar $\rightarrow$ Depo ve kargo ekibine Excel üzerinden sorar $\rightarrow$ Depo 2–3 iş gününde dönüş yapar $\rightarrow$ 4–5. iş gününde manuel onay/ret verilir.
* **Gelecek Süreç (To-Be — Yapay Zeka Destekli Akış):**
  1. **Ön Kural & Kalite Kontrolü:** Sistem önce 14 günlük yasal iade süresini (FR-02) ve fotoğraf bulanıklığını (FR-03) denetler.
  2. **AI Görüntü İşleme & Tersine Görsel Arama:** Yüklenen fotoğraf internette taranarak sahte/stok görsel olup olmadığı belirlenir (FR-04) ve hasar skoru hesaplanır.
  3. **3 Hatlı Otomatik Karar Noktası (XOR Gateway):**
     * 🟢 **Yeşil Hat (Otomatik Onay):** Hasar $\ge$ %85, fotoğraf net ve tutar $<$ 5.000 TL ise anında onaylanır, Kargo API ile ücretsiz kod üretilir ve WMS depo sistemine kaydedilir.
     * 🟡 **Sarı Hat (Müşteri Hizmetlerine Aktarım — Human-in-the-Loop):** AI güven skoru %50–%84 arasındaysa, sipariş tutarı $\ge$ 5.000 TL ise (aldatıcı fotoğraf yüklense dahi) veya müşteri "Ürün Elime Ulaşmadı" seçtiyse talep AI analiz raporuyla temsilci ekranına aktarılır.
     * 🔴 **Kırmızı Hat (Otomatik Ret):** İade süresi ($>$ 14 gün) geçmişse veya ($<$ 5.000 TL siparişte) internetten indirilmiş sahte fotoğraf tespit edilirse talep gerekçesiyle otomatik reddedilir.

## 📋 Öne Çıkan İş Gereksinimleri (BRD Özeti)

* **FR-01 (Self-Servis İade Kaydı):** Müşterinin siparişinden ürün seçerek JPEG/PNG formatında fotoğraf yüklemesi.
* **FR-02 (14 Günlük Süre Kuralı):** Yasal süresi dolan siparişlerin AI modeli çalıştırılmadan reddedilmesi (sunucu maliyeti optimizasyonu).
* **FR-03 (Bulanıklık Kontrolü):** Bulanık fotoğraf yüklendiğinde müşteriden anlık bildirimle yeniden yükleme istenmesi.
* **FR-04 (Web Sahtecilik Taraması):** Ürün fotoğrafının internet indekslerinde araştırılarak sahte olup olmadığının tespiti.
* **NFR-01 (Yükleme ve Boyut Sınırı):** Sistem optimizasyonu için talep başına **maksimum 3 fotoğraf** ve fotoğraf başına **maksimum 5 MB** sınırı.
* **NFR-02 (Performans):** Yapay zeka analizinin **en geç 5 saniye içinde** sonuç döndürmesi.

## 🧩 Yapay Zeka Uç Durumları (Edge Cases) ve Kabul Kriterleri (Gherkin)

* **EC-01 — Kadrajda Yabancı Ürün Görünmesi:** Müşteri ürün fotoğrafını gönderirken kamerada iade edilecek ürünün yanında yabancı başka bir ürün daha görünürse ve nesne güven skoru %85'in altına düşerse, sistem müşteriden ürünü düz bir zeminde tek başına tekrar çekmesini ister.
* **EC-02 — Ürünün Müşteriye Hiç Ulaşmaması (Kayıp Kargo):** Müşteri ürünün kendisine ulaşmadığını belirttiğinde fotoğraf yükleme zorunluluğu kaldırılır; sistem doğrudan Kargo Takip API verisini çekerek talebi müşteri hizmetlerine aktarır.
* **AC-01 — 5.000 TL Üzeri ve Aldatıcı Fotoğraf Kuralı:**
  * **Diyelim ki (Given):** İade tutarı 5.000 TL ve üzeri olan bir sipariş seçildiğinde,
  * **Olduğunda (When):** Müşteri sisteme aldatıcı/şüpheli bir fotoğraf yüklediğinde,
  * **Olmalıdır (Then):** Yapay zeka talebi doğrudan reddetmeyip analiz verileriyle (`hasar_yuzdesi`, `sahtecilik_yuzdesi`, `bulaniklik_durumu`) beraber müşteri hizmetlerine aktarmalıdır.

## 🤝 Ekipler Arası Hizalama ve Canlıya Geçiş (Rollout) Stratejisi

* **Veri Bilimi (AI) Ekibi Çıktısı:** Model inceleme sonrasında yazılım ekibine `onay_ret_onerisi`, `hasar_yuzdesi`, `sahtecilik_yuzdesi` ve `bulaniklik_durumu` verilerini JSON formatında döndürür; tüm veriler denetim izi ve modelin yeniden eğitimi için kayıt altına alınır.
* **Yazılım (Frontend/Backend) Ekibi Çıktısı:** Müşteri ekranı, Temsilci ekranı, Temsilci–AI entegrasyon ekranı ve Kargo Kodu / Kargo Takip API bağlantılarını geliştirir.
* **Ürün Yöneticisi (PM) ile Canlıya Geçiş Kararı:** Sistem tüm kullanıcılara aynı anda açılmaz; önce **kullanılabilirlik (user usability)** testi için küçük bir kullanıcı grubuna **Beta sürüm** olarak verilir, tespit edilen eksikler giderildikten sonra tam canlıya geçiş yapılır.

## 👩‍💻 İletişim

* **Hazırlayan:** Beyza Pamuk — Bilgisayar Mühendisliği & İş Analisti Adayı
* **Sertifika:** Microsoft Business Analysis Fundamentals (Coursera)
