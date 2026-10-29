# Mobil Programlama - Ödev 1: Bitki Kayıt ve Giriş Ekranı

Bu proje, Android platformunda **ConstraintLayout**, **alt layout hiyerarşileri (LinearLayout, CardView)** ve **zincirleme (Chain)** mimarisi kullanılarak geliştirilmiş bir mobil arayüz uygulamasıdır.

## 📱 Ekran Özellikleri ve Tasarım Blokları

Uygulama arayüzü, kök öğe olarak `ConstraintLayout` altında gruplandırılmış 3 ana bloktan ve alt layoutlardan oluşmaktadır:

### 1. Görseller Bloğu (`group_images`)
- Kart görünümü (`CardView`) içerisinde yatay (`LinearLayout` - `horizontal`) olarak yapılandırılmıştır.
- 4 adet bitki/doğa temalı görsel (`ImageView`) yan yana eşit genişlik dağılımı (`layout_weight="1"`) ve `centerCrop` ölçekleme ile yerleştirilmiştir.
- Tüm görseller vektörel formatta (`res/drawable/img_plant_*.xml`) hazırlanmıştır.

### 2. Kullanıcı Kayıt Bloğu (`group_register`)
- Ayrı bir `CardView` içerisinde dikey (`LinearLayout` - `vertical`) olarak gruplandırılmıştır.
- **Giriş Alanları:**
  - **Ad Soyad:** Kişi adı ve kelime baş harfleri büyük (`textPersonName|textCapWords`)
  - **E-posta Adresi:** E-posta klavye tipi (`textEmailAddress`)
  - **Yaş:** Sayısal klavye (`number`)
- **Kayıt Ol Butonu:** Özel yuvarlatılmış köşe yarıçapına (`24dp`) ve koyu yeşil/teal renge (`#006D5B`) sahip buton tasarımı (`bg_btn_register.xml`).

### 3. Kullanıcı Giriş Bloğu (`group_login`)
- Ayrı bir `CardView` içerisinde dikey (`LinearLayout` - `vertical`) olarak gruplandırılmıştır.
- **Giriş Alanları:**
  - **Kullanıcı Adı:** Standart metin girişi (`text`)
  - **Şifre:** Gizli karakter girişi (`textPassword`)
- **Giriş Yap Butonu:** Özel yuvarlatılmış mavi renge (`#1976D2`) sahip buton tasarımı (`bg_btn_login.xml`).
- **Şifremi Unuttum Bağlantısı:** Ortalanmış, kalın mavi tipografi ile hazırlanmış metin butonu.

---

## ⛓️ Zincirleme (Constraint Chain) Mimarisi

Kök `ConstraintLayout` içerisinde yer alan 3 ana grup (`group_images`, `group_register`, `group_login`) dikey bir zincir ile birbirine bağlanmıştır:
- Zincirleme stili olarak `app:layout_constraintVertical_chainStyle="spread_inside"` kullanılmıştır.
- Böylece en üstteki görsel bloğu ve en alttaki giriş bloğu ekran sınırlarına hizalanırken, aradaki kayıt bloğu ekran yüksekliğine göre dengeli bir şekilde ortalanmaktadır.

---

## 🎨 Kaynak Yönetimi (Values)

Projedeki hiçbir metin, renk veya boyut arayüz dosyalarında elle (hardcoded) yazılmamış; tamamen Android kaynak klasörlerinden dinamik olarak çekilmiştir:

- **Metinler (`res/values/strings.xml`):** Tüm hint (ipucu) metinleri, buton yazıları ve erişilebilirlik açıklamaları string kaynakları olarak tanımlanmıştır.
- **Renkler (`res/values/colors.xml`):** Kart arka planı, ekran arka planı, buton renkleri, metin ve çizgi renkleri palet halinde tanımlanmıştır.
- **Boyutlar (`res/values/dimens.xml`):** Padding, margin, buton yükseklikleri, köşe radyüsleri ve yazı boyutları dimens dosyası üzerinden yönetilmektedir.
- **Temalar (`res/values/themes.xml`):** Sistem çubuğu (status bar) renk uyumu ve pencere arka planı tema üzerinden yapılandırılmıştır.

---

## 🛠️ Teknolojiler ve Kütüphaneler

- **Dil:** Kotlin
- **Minimum SDK:** 24 (Android 7.0)
- **Target / Compile SDK:** 37
- **UI Toolkit:** Android Views (XML), `ConstraintLayout 2.2.2`, `CardView 1.0.0`
- **Sistem Uyumluluğu:** Edge-to-Edge (`WindowInsetsCompat`)
