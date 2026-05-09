# Automatic Cut Lite - Türkçe

Automatic Cut Lite, videolarınızdaki sessizlikleri, nefesleri ve uzun boşlukları otomatik olarak tespit edip kesen ücretsiz ve açık kaynaklı bir Adobe Premiere Pro eklentisidir.

[Click here for English documentation](README.md)

---

## Temel Özellikler

* **Akıllı Sessizlik Tespiti:** Ayarlanabilir dB eşiklerine göre nefes ve sessizlik aralıklarını milimetrik olarak tespit etmek için FFmpeg kullanır.
* **Çoklu Kanal Parçalayıcı:** İç İçe Sekans (Nested Sequence) kullanmadan tüm video ve ses kanallarını kusursuz bir şekilde keser.
* **Otomatik Yedekleme:** Kesimleri uygulamadan önce otomatik olarak kopyasını çıkararak orijinal sekansınızı korur.
* **Özel Geçiş Payı:** Robotik (sert) kesimlerden kaçınmak için kelimelerden önce ve sonra doğal nefes alma payı bırakmanıza olanak tanır.

## Gereksinimler

* **Windows İşletim Sistemi**
* **Adobe Premiere Pro** (Güncel sürümlerle uyumludur, 2026/24.x için geliştirilmiştir)
* **FFmpeg** (Yüklenmiş ve Windows Sistem PATH'ine eklenmiş olmalıdır)

---

## Kurulum Rehberi

### 1. Adım: FFmpeg'i Yükleyin

1. Windows için FFmpeg'i indirin. Ben [BtbN sürümünü](https://github.com/BtbN/FFmpeg-Builds/releases) kullandım ancak hangisi olduğu fark etmeyecektir.
2. İndirdiğiniz klasörü `C:` sürücünüze çıkartın (Örn: `C:\ffmpeg`).
3. Windows Başlat Menüsünü açın ve **Ortam Değişkenleri** (Environment Variables) yazıp aratın.
4. **Sistem ortam değişkenlerini düzenleyin** seçeneğine tıklayın -> **Ortam Değişkenleri** butonuna basın.
5. *Sistem değişkenleri* altında **Path**'i bulun, **Düzenle**'ye tıklayın ve yeni bir satır ekleyin: `C:\ffmpeg\bin`
6. Komut İstemini (`cmd`) açın ve çalıştığını doğrulamak için `ffmpeg -version` yazın.

### 2. Adım: Premiere Pro Hata Ayıklama Modunu Etkinleştirin

*(İmzasız eklentiler için gereklidir)*

1. Windows Başlat Menüsünü açın ve Kayıt Defteri Düzenleyicisi'ni açmak için `regedit` yazın.
2. Şu yola gidin: `HKEY_CURRENT_USER\Software\Adobe\CSXS.12`
*(Not: Premiere sürümünüze bağlı olarak bu sayı 11, 12 veya 13 olabilir. En yüksek sayı hangisiyse onun için bu işlemi yapın).*
3. Sağ taraftaki boş panele sağ tıklayın -> **Yeni** -> **Dize Değeri** (String Value).
4. Adını `PlayerDebugMode` yapın ve değerini `1` olarak ayarlayın.

### 3. Adım: Eklentiyi Kurun

1. [Bu repoyu indirin.](https://github.com/barbarpalvin/AutomaticCut/releases/tag/v1.0.0)
2. `Automatic Cut Lite` klasörünü kopyalayın.
3. Adobe CEP eklentileri klasörüne yapıştırın. İlk yolu deneyin; eğer yoksa veya çalışmazsa ikinciyi kullanın:

* `C:\Program Files (x86)\Common Files\Adobe\CEP\extensions\`
* **VEYA** `C:\Program Files\Common Files\Adobe\CEP\extensions\` *(Bende bu çalışıyor, aradaki farktan emin değilim)*

---

## Nasıl Kullanılır?

1. Premiere Pro'yu açın.
2. Üst menüye gidin: **Pencere (Window)** -> **Eklentiler (Extensions)** -> **Automatic Cut Lite**.
3. Sekansınızda **ANA SES** klibini (konuşma sesinin olduğu klip) seçin. *Tüm kanalları seçmeyin, sadece ana sesi seçin.*
4. Eklenti panelinden Sessizlik Eşiği (dB) ve geçiş paylarını ayarlayın. *(Varsayılan profil gayet iyi çalışmaktadır)*
5. **"1. Analiz Et"** butonuna tıklayın. Sessizlik listesinin dolmasını bekleyin.
6. **"2. Kesimleri Uygula"** butonuna tıklayın.
7. Eklenti mevcut sekansınızı yedekleyecek ve kusursuzca kesilmiş bir zaman çizelgesi oluşturacaktır!

---

## Bilinen Sorunlar ve Çözümler

* **Kesimler Arası Minik Boşluklar:** Bazen yeni oluşturulan sekansta kesimler arasında çok küçük boşluklar kalabilir.
**Çözüm:** Premiere Pro üst menüsünden `Sequence` -> `Close Gaps` seçeneğine tıklayarak bunları kolayca temizleyebilirsiniz.
* **Çoklu Kamerada Ufak Senkron Kaymaları:** Birden fazla kamera açısıyla çalışırken, kanallardan biri zaman çizelgesinin belirli bölümlerinde çok küçük senkronizasyon kaymaları yaşayabilir.
**Çözüm:** Diğer klibin kesim noktalarını referans alarak o belirli kısımları manuel olarak yeniden senkronize edebilirsiniz. *Gelecek sürümlerde bu sorunu düzeltmek için bir güncelleme üzerinde çalışıyorum.*
