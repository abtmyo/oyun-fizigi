# 📊 Ödev 1: Gaussian Dağılımı ve IQ Görselleştirmesi

## 🎯 Amaç
Bu ödevin amacı, **The Nature of Code - Bölüm 0** kapsamında öğrendiğimiz "Rastgelelik" ve "Normal Dağılım" (Gaussian Distribution) kavramlarını pekiştirmektir. `randomGaussian()` fonksiyonunu kullanarak sanal bir popülasyonun IQ skorlarını simüle edecek ve verilerin "Binning" (Gruplama) yöntemiyle nasıl bir Çan Eğrisi (Bell Curve) oluşturduğunu görselleştireceksiniz.

### 🔭 Örnek Program

* Bu ödevde istenen türde programın üretebileceği çıktı videoya alınmıştır. İlgili videoyu https://youtu.be/VURMTyL7fnU bağlantısından izleyebilirsiniz.
* Nature of Code kitabında uniform (düzgün) dağılım için benzer mantıkla yazılmış olan kodu https://natureofcode.com/random/#example-02-a-random-number-distribution bağlantısından inceleyebilirsiniz.

## 📘 Konsept: "Bin" (Grup) Nedir?
IQ skorları teorik olarak ondalıklı (floating point) sayılardır (örn: 100.45, 98.99). Ancak biz bunları bir çubuk grafiğe dökmek istiyoruz. Bunun için sayıları tamsayı gruplarına (bins) ayırmalıyız.

* **Bin Genişliği:** Bu ödevde her bir grup aralığını **1** kabul edeceğiz.
* **Örnek:** 100.00 ile 100.999... arasındaki tüm sayılar IQ puanı  **"100"** olan kutuya (bin) düşmelidir.
* **İndeks Yönetimi:** Eğer grafiğimiz en düşük 50 IQ'dan başlıyorsa, dizimizin 0. elemanı (`counts[0]`) 50 IQ'yu temsil etmelidir. Yani;
    * IQ 50 -> Dizi İndeksi 0
    * IQ 100 -> Dizi İndeksi 50
    * IQ 150 -> Dizi İndeksi 100

## 🚀 Görev Tanımı
p5.js kullanarak interaktif bir veri görselleştirmesi hazırlamanız beklenmektedir. Simülasyon, her karede (frame) yeni bir rastgele IQ skoru üretmeli ve ilgili "bin"i artırmalıdır.

### Teknik Gereksinimler

#### 1. Veri Yapısı ve Offset Mantığı
* **Sınırlar:** Simülasyonunuzun minimum (`minIQ`) ve maksimum (`maxIQ`) sınırlarını değişken olarak belirleyin. (Öneri: Min: 60, Max: 150).
* **Toplam Bin Sayısı:** Dizinizin boyutu, bu iki sınır arasındaki fark kadar olmalıdır (`totalBins = maxIQ - minIQ + 1`).
* **Offset (Kaydırma):** Ürettiğiniz IQ skoru, diziye işlenirken `minIQ` değeri kadar kaydırılmalıdır.
    * *Formül:* `index = floor(randomIQ - minIQ);`

#### 2. Görselleştirme ve Dinamik Genişlik
Grafiğiniz, belirlediğiniz `minIQ` ve `maxIQ` aralığı ne olursa olsun tuvali (canvas) tam doldurmalıdır.
* **Bar Genişliği (w):** Çubukların genişliğini elle "5px" gibi sabit vermeyin. Toplam bin sayısına göre dinamik hesaplayın.
    * *Formül:* `w = width / totalBins;`
* Bu sayede IQ aralığını değiştirdiğinizde (örneğin 0-200 yaptığınızda) çubuklar otomatik olarak incelip ekrana sığacaktır.

#### 3. Normalizasyon (Yükseklik Ayarı)
En çok tekrar eden IQ skoru (tepe noktası), simülasyon ne kadar uzun sürerse sürsün ekrandan taşmamalıdır.
* Dizi içindeki en yüksek değeri (en çok rastlanan IQ puanı) bulun.
* Her bir çubuğun yüksekliğini çizerken bu değere göre oranlayın (`map()` fonksiyonu kullanabilirsiniz).
* Çizim yaparken map() fonksiyonunu kullanarak, o anki çubuğun yüksekliğini, en büyük değere göre oranlayın.

Sonuç: En yüksek sütun her zaman ekranın belirli bir yüksekliğinde (örneğin %90'ında) sabit kalmalı, diğer sütunlar ona göre oranlanmalıdır. Simülasyon 1 saat de çalışsa grafik ekrandan taşmamalıdır.

## 📝 Adım Adım Kodlama Rehberi

1.  **Değişkenler:** `setup` dışında `counts` dizisini, `minIQ`, `maxIQ` değişkenlerini tanımlayın.
2.  **Kurulum (Setup):**
    * Toplam bin sayısını hesaplayın.
    * `counts` dizisini bu boyutta oluşturun.
    * `w` (genişlik) değerini `width / toplamBinSayisi` olarak hesaplayın.
3.  **Simülasyon (Draw Döngüsü):**
    * **Üretim:** `randomGaussian(mean, sd)` ile bir sayı üretin (Ort: 100, SD: 15).
    * **Filtreleme:** Eğer sayı `minIQ` ve `maxIQ` aralığı dışındaysa, işlemi yok sayın (dizi sınırlarını aşmamak için).
    * **İndeksleme:** Sayıyı tamsayıya çevirin ve `minIQ` çıkararak doğru indeksi bulun:
        `let index = floor(num) - minIQ;`
    * **Artırma:** `counts[index]` değerini 1 artırın.
4.  **Çizim:**
    * Bir döngü ile tüm diziyi gezin.
    * X konumu: `i * w`
    * Y konumu: `height - barHeight` (p5.js koordinat sistemi gereği).
    * `rect()` ile çubuğu çizin.

## 📤 Teslim Talimatları

Bu ödevi tamamlamak için **p5.js Web Editor** kullanabilirsiniz.

1.  Aşağıdaki GitHub Classroom davet linkine tıklayarak ödev reponuzu oluşturun:
    * **Davet Linki:** https://classroom.github.com/a/euMjHST8
2.  p5.js Web Editor üzerinde kodunuzu yazın.
3.  Projenizi kaydedin (Save).
4.  Davet linki ile oluşturulan repodaki `README.md` dosyasını düzenleyin ve projenizin linkini yapıştırın.
5.  Değişiklikleri `Commit` edin.

## 📜 Örnek README İçeriği

**Proje Linkim:**
[p5.js Web Editor linkinizi buraya yapıştırın]

---

## ⏰ Son Teslim Tarihi
**Tarih:** 1 Aralık 2025, Saat: 23:59
* *Geç kalan ödevler değerlendirmeye alınmayacaktır.*
* *Bu ödev bireysel yapılacak ve ödev kodu yapay zekaya yazdırılmayacaktır.*


Başarılar!
