********
Kalıplar
********

Gerçek tür olmayan, yani sanal bir kavram olan kalıplar tür kavramındaki 
tasarım eksiğini kapamayı amaçlar. 

Mesela, C dilinde en basit yapı türlerinden olan zincirler için 
her bir farklı türdeki zincir elemanı için yeniden tür tanımlamak zorunda kalıyoruz. 

Dahası C++ ve Rust gibi dillerde elimizde var olan ve yapısı, boyutu, sıralaması 
belirgin olan türler taçlandırılıyor ve türün boyutu ya da sıralaması değişebiliyor. 
Bu konuda biz yazılımcıların bu dillerin tanıştırdığı harika özelliği suistimal etmemizin 
de payı tabi ki yadsınamaz ama sistem yazılımcıları açımızdan çok ciddi bir 
belirsizlik ve bir takım hata ayıklamalar samanlıkta iğne aramaya dönüşüyor. 

Bu iki soruna karşılık Örs dili kalıp kavramını öne sürdü. Böylece,
'kalıp' kavramı vasat türler 
kavram bütünlüğünü, yapısal katılığını korurken kalıplar aracılığıyla 
hem tanım tekrarının 
önüne geçebilmek hem de biz sistem yazılımcılarının haklı 
takıntılarına çözüm üretmeyi amaçlıyor.

.. code:: 

  kalıp Dal x 
  {
    Öz       x;
    Önceki  *Dal'x; 
    Sonraki *Dal'x;
  }

  kalıp Zincir x 
  {
    boyut t32;
    Baş *Dal'x; 
    Son *Dal'x;
  }

Yukarıdaki örnek Örs'ün zincir kütüphanesinden alıntı. Basitçe anlaşılacağı üzere 
kalıp 'zincir' ne olduğu bilinmeyen 'x' türü ile taçlandırılana kadar derleyici hafızasında 
özel bir sanal tanım olarak yer alıyor. Genel yapısı belirgin olsa da boyutu belli olmadığı
için gerçek bir tür değil ve tamamen sanal. 

Kalıplar herhangi değişken ya da değerin türünü belirlerken anlam kazanıyor. 
Mesela yukarıdaki zinciri tam türüyle taçlandıralım. 

.. code:: 

  iş ZincirÖrneği 
  {
    değer rakamlar Zincir'tam;  
  }

Buyrun artık elimizde canlı, tam türüyle taçlandırılmış zincir türü var. 

---------------

Kalıp işlemler: 
^^^^^^^^^^^^^^^

Nam-ı diğer sanal işlemler. Malûmunüz üzere kalıplar sanal olduğu için 
onlara bağlanan işlemler de sanal olur. Yukarıdaki örneği devam ettirelim: 

.. code:: 

  öz Zincir'x 
  sanal iş Ekle Veri x: x 
  {
    Dal := temiz(%*öz.Baş); 
    Dal->Öz = Veri;
    eğer öz.boyut: 
    {
      Dal->Önceki     = öz.Son; 
      öz.Son->Sonraki = Dal; 
      öz.Son          = Dal; 
    }
    değilse
    {
      öz.Son = Dal; 
      öz.Baş = Dal; 
    }
    öz.boyut++;
    dön Dal->Öz;
  }


  iş ZincirÖrneği 
  {
    değer rakamlar Zincir'tam;  

    her değer i tam = 0; i < 10; i++: 
      rakamlar.Ekle(i);
  }

------------

Taçlar ve Donatımlar: 
^^^^^^^^^^^^^^^^^^^^^

Aşağıda çok kullandığımız çizelge veri türü var. 

.. code:: 

  kalıp kök x,y
  {
    Sıradaki *kök'x,y;
    hash      d32;
    ad        x; 
    öz        y;
  }

  kalıp k x,y 
  {
    boyut      tam; 
    hacim      doğal; 
    yığın      dizi::k'*kök'x,y;
    Nesneler **kök'x,y;
  }

  iş DonatımÖrneği 
  {
    değer sözlük k'metin,tam;
  }

Bu örneğin içeriği değişebilir ve konumuz dışında ama 
fark ettiğiniz üzere x ve y olası türleri sanki işlemlerdeki 
değişken kavramı gibi davranıyor.
Göze öyle görünse de gerçekte tabi ki de kesinkes öyle değil. 
Burada bu kavram çatışmasının önüne geçmek için kalıpların kabul ettiği olası tür simgelerini
'taç' olarak adlandırmayı ve kavramlandırmayı seçtik.

Herhangi bir kalıp ikiden fazla türle taçlandırılamaz ve o şekilde tanımlanamaz. 
İkiden fazla tacın aslında gereksiz olduğu bir yana Örsün tasarım ilkeleriyle de tutarlıdır. 
Yani Örs mantığına göre siz kalıp için ikiden fazla taç tanımlamışsanız sizin kalıbınızda bir 
sorun vardır. 

Mesela diyelim ki yukarıdaki 'kök' kalıbı 3 taç kabul ediyor. 

.. code:: 

  kalıp kök x,y
  {
    Sıradaki *kök'x,y;
    hash      z;
    ad        x; 
    öz        y;
  }

Bu örnekte bu kalıp belli ki çizelge algoritması tarafından kullanılacak ve 'hash' üyesinin 
bit genişliği algoritma için önemli zira diyelim ki d64 türünde olsaydı farklı sabit ya da 
algoritma kullanmanız gerebilirdi. 
Evet değişken doğalı sözlük algoritmaları var ama 
'k' veri türü o değişken doğalı algoritmayla uyum sağlayamaz. Yani ? Yani kalıp tanımında sorun var.

Örs'te kalıp da dahil tüm diğer kavramları olabildiğince doğrusal düşünmek istiyoruz. 
İkili tacı sakın küçümsemeyin. O iki tacın içine yüz tane farklı iç içe geçmiş donatılmış tür 
yerleştirebilirsiniz ama eğer veri türlerini bu şekilde saçaklandırma huyunuzun 
Örs'ün kendi tasarım kaidelerini çiğneyip desteklemesini beklemeyiniz. 

Donatım kavramı ise başlık altındaki misalde görüldüğü üzere kalıpların türe dönüştüğünde 
aldığı olası türlere atıfta bulunuyor. 
Malûm örnek için metin ve tam sayı sözlüğü değeri 'k' kalıbı 'metin' ve 'tam' türleri ile donatılmış.

Peki bu iki muğlak kavramı sanal işlemler için de kullanabilir miyiz ? 
Buradaki uygulamasını kabul etmediğimiz takdirde, elbette. Farkı ise sanal 
işlemlerde tıpkı işlemler gibi 16'dan fazla değişken almazlar 
ve bu değişkenlerin muğlak türlerine hitaben 'taç'; 
türü belirlenmiş, yani çağrılmış, hallerine hitaben 'donatım' kavramlarını 
bire bir olmamak şartıyla fevkâlade kullanabiliriz.



