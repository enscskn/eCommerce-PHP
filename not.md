# E-Ticaret Projesi Detaylı Notlar

## 1. Proje Hakkında Genel Bakış ve Yapı

### Proje Yapısı
```
eticaret/
├── index.php          # Ana giriş dosyası
├── kutuphane/         # Yardımcı fonksiyonlar ve sınıflar
├── sablonlar/         # Site şablonları
├── yonetim/           # Yönetim paneli
└── nbproject/         # NetBeans proje dosyaları
```

### nbproject Klasörü ve Dosyaları
- NetBeans IDE tarafından oluşturulan, projeye özel ayarları ve yapılandırmaları içeren sistem klasörüdür. Kodun çalışmasına doğrudan etkisi yoktur, geliştirme ortamı için kullanılır.
- **project.xml**: Proje ile ilgili temel bilgiler ve yapılandırma ayarları.
- **project.properties**: Derleme, çalışma ve diğer ayarlar.
- **private/**: Kullanıcıya özel ayarlar (private.xml, private.properties, config.properties).

---

## 2. Veritabanı Tasarımı ve Tablo Yapıları

### Kullanıcı, Ürün, Sipariş ve Sepet Tabloları
```sql
-- Kullanıcılar, adresler, kategoriler, ürünler, ürün resimleri, siparişler, sipariş detayları, sepet tabloları
-- ... (tüm tablo CREATE örnekleri buraya alınacak)
```

---

## 3. PHP Temelleri ve Projede Kullanımı

### Dosya Dahil Etme
```php
require_once 'kutuphane/ayarlar.php';z
require_once 'kutuphane/oturum.php';
require_once 'kutuphane/veritabani.php';
```

### Switch-Case ile Sayfa Yönlendirme
```php
switch($sayfa) {
    case 'uyelik':
        $baslik = "Üyelik İşlemleri";
        $icerik = "uyelik.php";
        break;
    // ... diğer case'ler
}
```

### Önemli Fonksiyonlar ve Yapılar
- Kategori işlemleri (kategoriMenu, altKategoriVar, urunKategoriler)
- Sepet işlemleri (sepetBilgisi, sepetEkle, sepetGuncelle)
- Sipariş işlemleri (siparisOlustur, siparisDetayEkle)
- Kullanıcı işlemleri (kullaniciGiris, kullaniciKayit, bilgiGuncelle)

---

## 4. Güvenlik Önlemleri

### SQL Injection, XSS, CSRF, Şifre ve Session Güvenliği
- Prepared statements ve input validation
- htmlspecialchars ile XSS koruması
- password_hash ve password_verify ile şifre güvenliği
- CSRF token kontrolü
- Session başlatma, kontrol ve sonlandırma

---

## 5. Hata Yönetimi

### Try-Catch, Form Doğrulama, Dosya Yükleme Kontrolü
- PDOException ile veritabanı hatası yakalama
- Form alanı ve e-posta doğrulama
- Dosya uzantısı ve türü kontrolü

---

## 6. Yönetim Paneli

### Genel Yapı ve Modüller
- index.php: Ana giriş
- giris.php: Yönetici girişi
- cikis.php: Çıkış işlemleri
- kategori_islemleri.php: Kategori yönetimi
- urun_islemleri.php: Ürün yönetimi
- urun_ozellikleri.php: Ürün özellikleri
- urun_resimleri.php: Ürün resim yönetimi
- siparisler.php: Sipariş yönetimi

### AdminLTE dist ve plugins Klasörleri
- **dist/**: Temel stil, JS ve görseller
- **plugins/**: Select2, jQuery, FontAwesome, Bootstrap gibi ek kütüphaneler

### Oturum Yönetimi
- Yönetici girişi, session oluşturma, çıkış ve güvenlik

### Navigasyon ve Şablonlar
- head.php, sablon.php, navbar.php, sidebar.php, footer.php
- Responsive tasarım, dinamik menü, kullanıcı paneli

---

## 7. Kullanıcı Arayüzü (Site Şablonları)

### Şablon Yapısı ve Temel Dosyalar
- head.php, footer.php, navigation.php, sablon.php
- $baslik, $icerik, SITE_SABLON, YONETIM_SABLON değişkenleri

### Kullanıcı, Ürün, Sepet, Sipariş, Adres, İletişim Sayfaları
- uyelik.php, uyelik_bilgileri.php, uyelik_guncelle.php
- urun_inceleme.php, sepet_islemleri.php, siparis_islemleri.php, siparis_listesi.php
- adres_islemleri.php, iletisim.php, cikis.php, anasayfa.php

---

## 8. JavaScript ve CSS Analizi

### site.js ve scripts.js
- Sepet işlemleri, AJAX, jQuery seçicileri, event handling, DOM manipülasyonu
- scripts.js: Boş, özel JS için hazır

### CSS Dosyaları
- styles.css, menu.css: Tema ve menü stilleri
- AdminLTE dist/css: Yönetim paneli teması

---

## 9. Sayfa Akışı ve Proje Mantığı

1. Kullanıcı siteye girer
2. index.php çalışır, gerekli dosyalar dahil edilir
3. GET parametresine göre sayfa belirlenir
4. İlgili sayfa yüklenir, işlemler yönetilir