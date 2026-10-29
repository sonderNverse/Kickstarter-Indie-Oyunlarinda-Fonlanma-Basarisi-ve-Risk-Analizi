# Kickstarter Bağımsız (Indie) Oyun Projelerinde Fonlanma Başarısı ve Risk Analizi

## Proje Amacı
Bu projenin amacı; bağımsız (indie) oyun geliştiricilerinin Kickstarter platformunda açacakları yeni oyun kampanyalarının fonlanma başarı ihtimalini ve risklerini makine öğrenmesi modelleriyle tahmin etmektir. Böylece hatalı bütçe ve kampanya süresi kararlarından kaynaklanan başarısızlık risklerinin en aza indirilmesi hedeflenmektedir.

## Problem ve Hedef Kullanıcı
- **Problem:** Bağımız oyun geliştiricileri finansal bütçe yetersizliğinden dolayı projelerini tamamlayamamaktadır. Kitlesel fonlama sitelerinde açılan kampanyaların büyük kısmı ise yanlış bütçe hedefi ve kampanya süresi seçimi gibi risk faktörleri yüzünden başarısızlıkla sonuçlanmaktadır.
- **Hedef Kullanıcı:** Kısıtlı bütçeyle oyun geliştiren ve Kickstarter platformundan destek arayan bağımsız oyun stüdyoları ve bireysel yazılımcılar.

## Kullanılacak Veri Seti
- **Veri Seti:** Kaggle üzerinden alınan "Kickstarter Projects" veri seti.
- **İncelenecek Özellikler:** Oyun kategorisi, hedef bütçe, ülke ve kampanya süresi.
- **Tahmin Edilecek Çıktı (Hedef):** Proje Durumu (Başarılı / Başarısız)
- **Kullanım Lisansı:** CC BY-NC-SA 4.0 (Kaynak göstermek ve eser sahibine atıf yapmak şartıyla ücretsiz akademik kullanım lisansı, ticari amaçla kullanılamaz)

## Kapsam
Proje 14 haftalık süre içince şu aşamaları tamamlayacaktır:
- Veri setinin indirilmesi ve EDA yapılarak eksik/hatalı satırların temizlenmesi.
- Veri sızıntısını engellemek için verinin %80 Eğitim %20 Test olarak ayrılması.
- Metinsel oyun kategorilerinin bilgisayarın anlayacağı sayısal verilere dönüştürülmesi.
- Logistic Regression, Random Forest ve Gradient Boosting makine öğrenmesi algoritmalarının eğitimi.
- Modellerin başarılarının sadece genel doğruluk oranıyla değil; Precision, Recall ve F1-Scor metrikleriyle karşılaştırılması.
- **[Fonksiyonel Olmayan Gereksinim]:** Yazılan Python kodunun VS Code terminalinde 2 saniyenin altında kararlı ve hızlı tahmin üretmesi.

## Kapsam Dışı
- Proje için hiçbir web sitesi arayüzü, mobil uygulama veya web formu yapılmayacaktır.
- Sistem sadece VS Code terminalden çalışacaktır.
- Canlı internet sitesinden anlık veri çekilmeyecektir. Tamamen indirilmiş mevcut veri seti kullanılacaktır.

## Varsayımlar
- Veri setinde yer alan geçmiş Kickstarter projelerinin fonlanma durumlarının (Başarılı/Başarısız) doğru etiketlendiği varsayılmıştır.
- Oyun kategorileri, hedef bütçe ve kampanya sürelerinin fonlanma başarısı üzerinde anlamlı birer ayırt edici özellik (feature) olduğu varsayılmaktadır.

## Ekip ve Roller
- **Azra Naz Savcı** · Developer (Geliştirici / Kod Sorumlusu) · @sonderNverse
- **AyşegülSencer** · İş Analisti (Süreç ve İletişim Sorumlusu) · @SleepyGoat7
- **Hatice Sevde Nurlu** · Tester & Dokümantasyon (Kalite ve Rapor Sorumlusu) · @sevdenurlu

# Kickstarter Indie Oyunlarında Fonlanma Başarısı ve Risk Analizi

## 1. Veri Seti Erişim Kılavuzu ve Veri Kataloğu
## Veri Seti Erişim Kılavuzu ve Veri Kataloğu
-**Veri Seti Kaynağı (Kaggle):** [ https://www.kaggle.com/datasets/kemical/kickstarter-projects ] 
-**Lisans Bilgisi:** Bu veri seti **CC BY-NC-SA 4.0** (Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International) lisansı ile korunmaktadır.

### Veri Değişkenleri Kataloğu (Data Dictionary)
Veri setimizdeki ana sütunların açıklamaları şunlardır:

| Sütun Adı | Veri Tipi | Açıklama |
| :--- | :--- | :--- |
| `ID` | Integer / String | Projeye ait benzersiz tanımlayıcı numara. |
| `name` | Text / String | Kickstarter'da yayınlanan projenin/oyunun adı. |
| `category` | Categorical | Projenin ait olduğu alt kategori (örn. Video Games, Tabletop Games). |
| `main_category` | Categorical | Projenin ana kategorisi (örn. Games, Technology, Film & Video). |
| `currency` | Categorical | Kampanyada hedeflenen para birimi (USD, GBP, EUR vb.). |
| `deadline` | Date / Time | Kampanyanın sonlanma/bitiş tarihi. |
| `goal` | Numeric (Float) | Proje için hedeflenen orijinal bütçe miktarı. |
| `launched` | Date / Time | Kampanyanın başlatıldığı/yayına girdiği tarih. |
| `pledged` | Numeric (Float) | Toplanan toplam fon miktarı (orijinal para biriminde). |
| `state` | Categorical | Kampanyanın son durumu (successful, failed, canceled, live, suspended). |
| `backers` | Integer | Kampanyaya destek veren / bağış yapan toplam kişi sayısı. |
| `country` | Categorical | Kampanyanın başlatıldığı ülke kodu (US, GB, CA vb.). |
| `usd_pledged_real` | Numeric (Float) | Toplanan fonun USD (Amerikan Doları) cinsinden dönüştürülmüş reel değeri. |
| `usd_goal_real` | Numeric (Float) | Hedef bütçenin USD cinsinden dönüştürülmüş reel değeri. |

## 2. Ön Literatür Taraması Tablosu

Kitlesel fonlama (crowdfunding) platformlarındaki projelerin başarısını etkileyen faktörler ve tahminleme yöntemleri üzerine yapılan temel akademik çalışmalar:

| Çalışma / Yazar | Araştırma Problemi | Kullanılan Veri Seti | Uygulanan Yöntem(ler) | Sınırlamalar ve Bulgular |
| :--- | :--- | :--- | :--- | :--- |
| **Mollick, E. (2014)**<br>*(The Dynamics of Crowdfunding)* | Kitlesel fonlama projelerinde başarıyı belirleyen temel dinamiklerin tespiti. | Kickstarter platformuna ait 48.000+ proje verisi | Tanımlayıcı İstatistikler, Regresyon Analizi | Proje hedef bütçesinin ve kampanya süresinin başarı üzerinde doğrudan etkili olduğu görülmüştür. |
| **Skirnevskiy vd. (2017)**<br>*(The entrepreneur matters...)* | Proje özelliklerinin ve kategorik dinamiklerin kitlesel fonlama başarısına etkisi. | Kickstarter Kampanya Arşivleri | İstatistiksel Korelasyon ve Regresyon Modelleri | Finansal hedeflerin yanı sıra kategori bazlı nitel etkenlerin de başarı oranını değiştirdiği kanıtlanmıştır. |
| **Etter, V. vd. (2013)**<br>*(Launch hard or go home: Predicting success on Kickstarter)* | Kickstarter projelerinin fonlanma başarısının istatistiksel olarak önceden tahmini. | Kickstarter Kapsamlı Veri Havuzu | Olasılıksal Modelleme ve Tahminleme | Hedef bütçe büyüklüğünün başarı ihtimalini ters yönde etkileyebileceği, doğru sınıflandırma gerektirdiği vurgulanmıştır. |

## 3. İlk Yöntem Gerekçesi (Baseline Model Seçimleri)

Projemizde bağımsız oyunların fonlanma başarısını tahmin etmek ve risk analizi yapmak amacıyla başlangıç modelleri (baseline) olarak **Logistic Regression**, **Random Forest** ve **Gradient Boosting** algoritmaları seçilmiştir. 

* **Akademik Gerekçe:** **Logistic Regression**, sınıflandırma problemlerinde doğrusal ilişkileri açıklayabilen yüksek yorumlanabilirliğe sahip temel bir referans model sunarken; **Random Forest** ve **Gradient Boosting** gibi topluluk (ensemble) öğrenme yöntemleri, oyun bütçesi, kategori ve süre gibi değişkenler arasındaki karmaşık ve doğrusal olmayan (non-linear) örüntüleri yüksek doğrulukla yakalayabilmektedir. Bu sayede modellerin performansları karşılaştırılarak en güvenilir risk analiz altyapısı kurulacaktır.


