=====
Ortak
=====

Tekil hafızanın çoğul değerler için kullanıldığı özel türlerdir. 

Ortak olarak isimlendirilmesinin nedeni özlerinde konumlar beklemeleridir.
Zira yazılımda konumu 'şey' değerine saklar ve sonrasında bu konumun aslında 
ne konumu olduğunu bilmeden tehlikeli sularda yüzerek işlemlerimizi yapabilirdik. 
Ortak konumun farklı türler için ortak kullanılan bir konum olarak düşünüldüğünü 
varsayarak bir çerçeve etrafında konumu yorumlar. 
Bu bakımdan 'şey' türünün kavram olarak daraltılmış halidir. 

C dilindeki 'union' kavramının Örs dilindeki dengidir. 

.. code:: 
  
  ortak çıktı 
  {
    sayı      t64; 
    harfler   t8[8];  
  }

  iş Örnek 
  {
    değer i çıktı;
    i.sayı = 0x0_41_42_43_44_45_46_47; 
    stdio::printf(
      "Konumlar:\n&i.sayı = %p\n&i.harfler\n"
      "metni = '%s'\n", 
      &i.sayı, i.harfler, i.harfler);
      //benim işlemcinin mimarisinde i.harfler GFEDCBA olarak görünüyor

    stdio::printf(
      "i          = %x\n"
      "harfler[0] = %x\n"
      "harfler[1] = %x\n"
      "harfler[2] = %x\n"
      "harfler[3] = %x\n"
      "harfler[4] = %x\n"
      "harfler[5] = %x\n"
      "harfler[6] = %x\n"
      "harfler[7] = %x\n", 
      i, 
      i.harfler[0],
      i.harfler[1],
      i.harfler[2],
      i.harfler[3],
      i.harfler[4],
      i.harfler[5],
      i.harfler[6],
      i.harfler[7]);
  }


Bu örneğin anlamsız olduğu düşünülebilir ki gerçekten de öyle. 
Tek amacı sayı ve harfler adlı üyelerin aynı konumu paylaştığını göstermek 
ama zaten ortakların yaygın kullanımı da bu şekilde olmaz. 
Genelde künyelendirilerek kullanılırlar. Mesela: 

.. code:: 
  
  ortak çıktı 
  {
    sayı      t64; 
    harfler  *t8;
    url      *t8;
    Metin    *metin;
  }

  sayaç seçimler 
  {
    Sayı = 1; 
    Harfler;
    Url; 
    Metin;
  }

  tür imge 
  {
    künye  t32; 
    içerik çıktı;
  }

Veri iskeletinden de anlaşılacağı üzere basitçe metin çözümleme türü tanımlanmış. 
Bu iskeleti derleyicilerden, dil sunucularına, veri tabanlarından, oyunlara her yerde kullanacaksınız. 
En az zincirler konusu kadar yaygın bir iskelet. 
