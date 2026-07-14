# DIY H-Field Probe & Pre-Compliance EMI Debugging

Selamlar! Bu projede, laboratuvar standartlarında binlerce dolar harcamadan, kendi yaptığımız bütçe dostu bir Near-Field H-Field (Manyetik Alan) Probu ile bir PCB üzerindeki EMI (Elektromanyetik Parazit) kaynaklarını nasıl nokta atışı tespit edebileceğimizi inceliyoruz.

---

Projenin Hikayesi ve Sorun:

Bir cihaz tasarladık, her şey harika çalışıyor. Peki ya görünmeyen dünyada neler oluyor?Cihazımız havaya veya kablolara istemediğimiz yüksek frekanslı sinyaller (parazit) yayıyor mu?
Sertifikasyon test merkezlerine (akredite laboratuvarlara) gidip ölçüm yaptırmak hem çok pahalı hem de zaman alıcıdır. Bu yüzden Pre-Compliance (Ön Uyumluluk) testlerini kendi masamızda yapmamız hayati önem taşır.
Ben de bu projede, kendi yaptığım basit bir koaksiyel kablo döngüsü (loop) ile Rohde & Schwarz FSV Spektrum Analizörünü bir araya getirdim. Tasarımdaki Buck Converter'ın bobinine yaklaştığım anda ekrandaki gürültü seviyesinin tavan yaptığını gözlemledim.

---
EMI (Elektromanyetik Parazit) Nedir ve Neden Önemlidir?

Elektromanyetik Uyumluluk (EMC), cihazınızın hem dış dünyadaki elektromanyetik gürültülerden etkilenmemesini (Immunity) hem de dış dünyaya parazit yaymamasını (Emission) ifade eder.
* Neden Önemlidir? Eğer kartınız standartların üzerinde EMI yayıyorsa, FCC veya CE gibi sertifikaları alamazsınız. Bu da ürününüzü yasal olarak satamayacağınız anlamına gelir.

---



