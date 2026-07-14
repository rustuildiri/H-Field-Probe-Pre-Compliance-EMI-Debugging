# DIY H-Field Probe & Pre-Compliance EMI Debugging

Selamlar! Bu projede, laboratuvar standartlarında binlerce dolar harcamadan, kendi yaptığımız bütçe dostu bir Near-Field H-Field (Manyetik Alan) Probu ile bir PCB üzerindeki EMI (Elektromanyetik Parazit) kaynaklarını nasıl nokta atışı tespit edebileceğimizi inceliyoruz.

* ![Setup1:](assets/screenshots/1.png)
---

Projenin Hikayesi ve Sorun:

Bir cihaz tasarladık, her şey harika çalışıyor. Peki ya görünmeyen dünyada neler oluyor? Cihazımız havaya veya kablolara istemediğimiz yüksek frekanslı sinyaller (parazit) yayıyor mu?
Sertifikasyon test merkezlerine (akredite laboratuvarlara) gidip ölçüm yaptırmak hem çok pahalı hem de zaman alıcıdır. Bu yüzden Pre-Compliance (Ön Uyumluluk) testlerini kendi masamızda yapmamız hayati önem taşır.
Ben de bu projede, kendi yaptığım basit bir koaksiyel kablo döngüsü (loop) ile Rohde & Schwarz FSV Spektrum Analizörünü bir araya getirdim. Tasarımdaki Buck Converter'ın bobinine yaklaştığım anda ekrandaki gürültü seviyesinin tavan yaptığını gözlemledim.


* ![Setup1:](assets/screenshots/2.png)
---
EMI (Elektromanyetik Parazit) Nedir ve Neden Önemlidir?

Elektromanyetik Uyumluluk (EMC), cihazınızın hem dış dünyadaki elektromanyetik gürültülerden etkilenmemesini (Immunity) hem de dış dünyaya parazit yaymamasını (Emission) ifade eder.
* Neden Önemlidir? Eğer kartınız standartların üzerinde EMI yayıyorsa, FCC veya CE gibi sertifikaları alamazsınız. Bu da ürününüzü yasal olarak satamayacağınız anlamına gelir.

---

Ölçüm Kurulum ayarları:
* Cihaz: Rohde & Schwarz FSV Signal Analyzer
* Frekans Aralığı: $150\text{ kHz} - 30\text{ MHz}$ (İletilen/Conducted EMI bölgesi başlangıcı için)
* RBW (Resolution Bandwidth): Standartlara uygun analiz için 9 kHz
* Mod: Clear Write (Canlı mod - probu yaklaştırıp uzaklaştırdıkça gürültü seviyesinin anlık değişimini görmek için)

---
Ne Gözlemledim?

Probu PCB üzerinde gezdirmeye başladım. Kartın diğer bölgelerinde sinyal oldukça sakinken, Buck Converter'ın güç bobininin (inductor) üzerine geldiğim anda spektrum analizöründeki sarı gürültü dalgasının (noise floor) aniden yukarı fırladığını gördüm.
Bu durum, bobin etrafındaki manyetik sızıntının (magnetic flux leakage) ve anahtarlama gürültüsünün en yüksek olduğu noktayı bize doğrudan kanıtladı.

---

PCB Tasarım Sürecinde Bu Bilgiyle Ne Yapacağız?

* Bu tespiti yaptıktan sonra kartı revizyona gönderirken şu önlemleri alabiliriz:
* Korumalı (Shielded) Bobin Kullanmak: Manyetik alanı içinde hapseden metal korumalı bobinler EMI'ı ciddi oranda düşürür.
* Loop Alanını Küçültmek: Anahtarlama akımının aktığı yolları (giriş kondansatörü, MOSFET ve diyot/bobin arasındaki döngüyü) fiziksel olarak olabildiğince küçük tasarlamak.
* Ground Plane (Toprak Düzlemi): Gürültülü yolların hemen alt katmanında kesintisiz bir toprak katmanı barındırarak dönüş akımlarının kendi yolunu bulmasını sağlamak.






