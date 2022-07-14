*******
Sayılar
*******


Bilgisayar dünyasındaki tüm veri türleri 
en sade haliyle ifade edilmiş sabit değerlerdir. 
Sabitlerdir ve bir değere atanıncaya kadar yaşadıkları konumları yoktur. 
  
Şimdi biraz hayal edin. 16 bit genişliğinde veri türü tanımladığınızda aslında yaptığınız şey; 
2^16 farklı birim tanımlamaktır. Çünkü sayılar deyince ortalama bir insanın aklına hesap gelebilir 
ama bizim için en önemli anlamı bu sayıların etiket gibi kullanılabilecek olmasıdır. Mesela ilk okul 
numaram 115'di. 115 numarası okul ortamında bana atıfta bulunuyordu. Işte bu yönüyle katı tanımlı sayı 
türlerinin varlığı sayısal tasarımda anlam kazanıyor. Veritabanlarından, işletim sistemlerine, 
devlet dairelerindeki belgelerden, okullara kadar her yerde var olan basit bir anlam. O da basitçe 
özlerinde birer atıflar olmalarıdır. Yani tanımladığımız benzersiz sayılar 
benzersiz nesne ya da öznelere atıfta bulunurlar. 

Örs'de tanımlı tüm sayı yapıtaşları C, C++ dilleri ile llvm aracılığı ile tam uyumludur. 
Zira öyle olmak da zorundadır. Çünkü yazılım dilleri uzayın derinliklerinde yalıtılmış
ortamlarda yaşamıyor. Aksine milyonlarca farklı birimle iletişim halindeler ve bu iletişimi 
kayıpsız yapabilmenin en basit yolu, tüm dillerde kullanılabilecek sade, bitlerle tanımlabilecek, 
türlerden geçmektedir. Zaten "dijital tasarım" denilen kavramın özü de tam olarak burasıdır. 

.. code:: 

  /*pascal haliyle:*/
  atmışDörtBitlikTamSayı := 55_st64;
  uzunSayılar            := 10_000_000_st32;  /*fark ettiyseniz alt tirelerin yerinin bir önemi yok*/ 
  okulNo                 := 2004_43_280_st32; /*mesela*/ 
  yaşım                  := 29;               /*t32 varsayılır*/ 
  oran32                 := 44.00_o32; 
  oran                   := 12.88             /*o64 varsayılır ve ondalık kısım nokta ile ayrılır*/;

  /*açık haliyle*/ 
  değer uzun d64   = 11_000_000;
  değer uzun64 d64 = 22_999_000_sd64; /*Aynı şey mi ? Evet. Peki ya sıradaki:*/ 
  değer u64 d64    = 22_990_1_st32; /*u64 değeri 64 bitlik doğal sayı olarak tanımlanıp atanan sabit değer çevrilir.*/
