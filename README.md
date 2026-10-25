# Kickstarter Bağımsız (Indie) Oyun Projelerinde Fonlanma Başarısı ve Risk Analizi

## Proje Amacı
Bu projenin amacı; bağımsız (indie) oyun geliştiricilerinin Kickstarter platformunda açacakları yeni oyun kampanyalarının fonlanma başarı ihtimalini ve risklerini makine öğrenmesi modelleriyle tahmin etmektir. Böylece hatalı bütçe ve kampanya süresi kararlarından kaynaklanan başarısızlık risklerinin en aza indirilmesi hedeflenmektedir.

## Ekip ve Roller
- **Azra Naz Savcı** · Developer (Geliştirici / Kod Sorumlusu) · @sonderNverse
- ** ** · İş Analisti (Süreç ve İletişim Sorumlusu) · @
- **Hatice Sevde Nurlu** · Tester & Dokümantasyon (Kalite ve Rapor Sorumlusu) · @sevdenurlu
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
