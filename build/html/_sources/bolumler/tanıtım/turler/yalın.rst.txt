*******************
Yalın tür tanımları 
*******************

Tekil gizli üyeleri olan türlerdir. 

Bir yönüyle her hangi bir türü yeniden adlandırma 
görevini üstlenirken; sıfatlarıyla güçlü bir kavrama evrilir. 
--------------
Basitçe: 

.. code:: 

  tür TamSayı tam; 

  sayı TamSayı 
  iş Yazdır 
  {
    stdio::printf("sayı: %d", sayı);
  }

Görüldüğü üzere varsayılan yapıtaşı 
'tamsayı' olarak tekrar tanımlanmış ve kendisine ait işlemler bağlanmış. 
Bu yönüyle yalın türlerin görevi;
aynı veri türlerini kullanan ama tamamen farklı algoritmaları
kullanan yazılımlarda kavramları belirgin yapmak 
ve yaygın türlere görevi olduğu ortamın amacına uygun görevler tanımlamaktır;

-------------------

.. code:: 

  tür Sayılar dizi::k'tam;
  
  sayılar Sayılar 
  iş Yazdır 
  {
    her i := 0; i < sayılar.boyut; i++;
      stdio::printf(
        "%d'inci sayı = %d", 
        i, sayılar.Öğe[i]);
  }
  
Bir diğer önemli konu ise kalıpları donatırlar. 
Kalıplara, tasarımları gereği, 
gerçek işlemler bağlanamaz. Yalın türler 
aracılığıyla donatıldıklarında kalıpların değer satırlıyla tekrar
tekrar tanımlanmasının önüne geçer ve 
kalıpların anlam bulduğu ortamda 
ilişkili işlemler ve algoritmalar bağlanabilir hale gelir. 

