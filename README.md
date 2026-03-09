# ServisPro – Android Kurulum Rehberi
Isıtma & Soğutma Teknik Servis Takip Uygulaması

---

## 📱 Uygulama Özellikleri
- Müşteri bilgileri (ad, telefon, e-posta, adres)
- Cihaz bilgileri (tür, marka, model, seri no)
- İşlem & malzeme listesi (otomatik toplam hesabı)
- Teknisyen & müşteri dokunmatik imzası
- **Firma logosu yükleme** (PDF'e otomatik eklenir)
- Profesyonel PDF oluşturma
- WhatsApp & E-posta ile PDF gönderme
- Servis geçmişi ve arama
- Firma bilgileri (ad, vergi no, web sitesi)

---

## 🛠️ Kurulum Adımları

### 1. Android Studio İndir
👉 https://developer.android.com/studio
(~1GB – ücretsiz)

### 2. Projeyi Aç
1. Android Studio'yu başlatın
2. **"Open"** butonuna tıklayın
3. Bu `ServisPro` klasörünü seçin
4. **"Trust Project"** deyin

### 3. Gradle Sync Bekleyin
- Sağ üstte dönen ikon kaybolana kadar bekleyin (~2-5 dakika)
- Alt çubukta "BUILD SUCCESSFUL" mesajını görün

### 4. Telefonu Bağlayın
1. Android telefonunuzda **Ayarlar → Telefon Hakkında → Derleme Numarası**'na 7 kez dokunun (Geliştirici Modu açılır)
2. **Ayarlar → Geliştirici Seçenekleri → USB Hata Ayıklama** → Açık
3. Telefonu USB ile bilgisayara bağlayın
4. "Bu bilgisayara güven?" sorusuna **"Evet"** deyin

### 5. Çalıştır
1. Android Studio'da üstteki cihaz seçiciside telefonunuzu seçin
2. Yeşil ▶️ **Run** butonuna tıklayın
3. Telefonda uygulama açılır!

### 6. APK Oluşturun (Başkalarıyla Paylaşmak İçin)
1. **Build → Build Bundle(s) / APK(s) → Build APK(s)**
2. APK dosyası: `app/build/outputs/apk/debug/app-debug.apk`
3. Bu dosyayı WhatsApp/mail ile başka telefonlara gönderebilirsiniz

---

## 📋 Kullanım

### Logo Yükleme
1. Uygulamada **Ayarlar** sekmesine girin
2. "Logo Seç" butonuna dokunun
3. Galerinizden firma logonuzu seçin (PNG/JPG)
4. **Kaydet**'e basın
5. Artık tüm PDF'lerde logonuz görünür!

### Servis Kaydı Oluşturma
1. Ana sayfada **+** butonuna veya "Yeni Kayıt"a dokunun
2. Müşteri ve cihaz bilgilerini doldurun
3. İşlem/malzeme satırlarını ekleyin
4. İmzaları alın
5. **Kaydet ve Oluştur**

### PDF Gönderme
1. Kayıt detayına girin
2. **PDF İndir** → Paylaşım menüsü açılır
3. **WhatsApp** → Direkt müşterinin numarasına mesaj + PDF
4. **E-posta** → PDF ekli mail hazırlanır

---

## ⚠️ Sorun Giderme

**"Gradle sync failed"** → İnternet bağlantınızı kontrol edin, tekrar sync deneyin

**"Device not found"** → USB Hata Ayıklama açık mı? USB kabloyu değiştirip deneyin

**"INSTALL_FAILED_..."** → Telefonda eski versiyonu silin, tekrar yükleyin

**OpenPDF kütüphanesi bulunamıyor** → `app/build.gradle` dosyasında şunu kontrol edin:
```
repositories { ... mavenCentral() ... }
implementation 'com.github.librepdf:openpdf:1.3.30'
```

---

## 📁 Proje Yapısı
```
ServisPro/
├── app/src/main/
│   ├── java/com/servispro/app/
│   │   ├── MainActivity.java          ← Ana sayfa
│   │   ├── NewServiceActivity.java    ← Yeni servis formu
│   │   ├── ServiceDetailActivity.java ← Servis detayı + gönderme
│   │   ├── SettingsActivity.java      ← Firma ayarları + LOGO YÜKLEME
│   │   ├── PdfGenerator.java          ← PDF oluşturma motoru
│   │   ├── SignatureView.java         ← Dokunmatik imza
│   │   ├── DataManager.java           ← Veri saklama
│   │   ├── ServiceRecord.java         ← Veri modeli
│   │   └── RecordAdapter.java         ← Liste adaptörü
│   └── res/
│       ├── layout/                    ← Ekran tasarımları
│       ├── values/                    ← Renkler, yazılar
│       └── drawable/                  ← Arka planlar
```
