======
Türler 
======

İşlemler nasıl bilgisayar dünyasının kalbinin attığı yerse;
türler de bu dünyanın iskeleti ve tamamlayanı. 

Örs bize tür konusunda geniş bir kavram yelpazesi sunuyor.
Kalıplar, yalınlar, ortaklar, künyeler ve daha nicesi ama, fakat, ve lâkin;
Tüm diğer kavramlar bu yazıda ele alınacak tür kavramının süslenmiş;
yani hazır yapılandırılmış hali. 

Türler özlerinde sıralıdır türler kümesidir. Kümesidir zira kendi kendisinin
üyesi olamaz. Kümesidir çünkü tanım tekrarı yapılamaz. 
Sıralıdır çünkü tüm sistem dillerinde olduğu gibi üyelerin 
sırası bit genişliğini ve bit sıralamasını belirler. 

Örs dilinde türler nesne tabanlı dillerle benzeşmez. 
C'deki 'struct' kavramının genişletilmiş halidir. 
Tıpkı C dilindeki bir tür tanımladığınızda nesne dosyasında 
nasıl yapılanacağı hayalinizde somutlaşıyorsa Örs'de de öyledir. 
Bu yönüyle Örs'deki tür soyutlaması makineye yakındır. 

.. code:: 

  tür Metin 
  {
    boyut     t32;
    hacim     t32; 
    _harfler *t8;
  }
  
Her ne kadar Örs nesne tabanlı yazılım tarıznı desteklemese 
ve de yapısalcılığı öne cıkarsa da Örs'de türlere işlem bağlamak mümkün. 

.. code:: 

  //yukarıdaki örneğin devamı 
  öz *Metin 
  iş Yaz Belge *stdio::FILE 
  {
    stdio::fprintf("metin: %s\n", öz->Metin);
  }

