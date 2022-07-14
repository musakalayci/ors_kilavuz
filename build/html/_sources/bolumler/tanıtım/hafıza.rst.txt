******
Hafıza
******


Yeni:
^^^^^
İşletim sisteminden istenilen boyutta yeni hafıza 
konumu istemek için kullanılan ifadedir. Sadece ve sadece 
tür ifadesini kabul ederler ve diğer ifadelerin ise türünü alıp
ona göre işlevlerini gerçekleştirirler. Mesela: 

.. code:: 

  değer Sayılar *tam = yeni(tam[20]); 
  // 20 X 4 baytlık dizinin konumunu dönecek 
  // ve bu konum sayılar değerinde tutulacak.x
  değer Matriks **tam = yeni(%Sayılar[20]);
  // Sayılar değerinin türü bir konum olduğu için 
  // (konum genişliği) x 20 baytlık bir konum dizisi dönecek ve matriks olacak.
  // ama farkettiğiniz üzere matriksin satırları boş.
  değer DoluMatriks **tam = yeni(tam[20, 20]);
  // bu satırda ise yeni ifadesi 20x20'lik tam sayı matriksi oluşturdu.
  
Yeni ifadesinin C dilindeki karşılığı hepimizin bildiği malloc işlemidir. Mesela:

.. code:: 

  değer Sayılar *tam = yeni(tam[20]);
  // yukarıdaki Örs satırı ile; aşağıdaki
  int* Sayılar = malloc(20 * sizedf(int));
  // C satırı özlerinde bire bir aynıdır.


Temiz:
^^^^^^
Yeni ifadesinden sonra işletim sisteminin yazılıma tahsis edeceği 
hafızanın içeriği bilinemez. Bu yüzden genelde C dilinde yazarken
hafıza ayrıldıktan sonra onu temizleriz. 
Tam bu noktada temiz ifadesi anlamlı oluyor. Mesela yukarıdaki örneği tekrar 
ele alalım:

.. code:: 

  değer Sayılar *tam = temiz(tam[20]);

Bu örnekte ise temiz ifadesinin anlamı 20X4 bayt genişliğinde 
sıfırlanmış tam sayı dizisidir.


Yenile:
^^^^^^^
İşletim sistemi tarafından öncesinde ayrılmış kaynağı daraltmak 
ya da genişletmek için kullanılır. C dilindeki karşılığı realloc işlemidir.

Sil:
^^^
İşletim sisteminin bize verdiği kaynağın görevi sona erdikten sonra 
eğer ki bilgisayar hafızasının veri çöplüğüyle dolmasını istemiyorsak;
kaynağı sahibine geri vermemiz gerekiyor. 

'Sil' imgesi bir satırdır ve bir değer dönmez. 

Silinen konum değerleri boşlanır. Yani konumun yeni sayısal değeri 0'dır.

**Mesela**:

.. code:: 
  
  değer Sayılar *tam = temiz(tam[20]);
  her i := 0; i < @tam[20]; i++: 
    stdio::printf("0 mı : %d\n", (Sayılar[i] == 0));
  /*
    sıfır olduğunu gösterdik ve işimiz bitti, 
    şimdi kaynağı geri verme zamanı. 
  */
  sil Sayılar;
  stdio::printf("Sayılar değerindeki konum : %p\n", Sayılar);
  /*
    Canlı hata verilmediyse arayüzde : 
    "Sayılar değerindeki konum : (nil)"
    gibi bir çıktı alınacaktır.
  */

Boşalt:
^^^^^^^
Görevi basitçe konuma gidip içeriğini sıfırlamaktır. 
İki farklı söz dizimi vardır. İlk söz diziminde;
İlk değişkeni konumken, 
ikincisi boşaltırken o konumda ne kadar ilerleyeceği bilgisidir.

Boşalt imgesi bir satırdır.

**Mesela**: 

.. code:: 

  değer Sayılar *tam = yeni(tam[20]);
  boşalt Sayılar, 20;

Sayılar dizisindeki tüm tam sayı hücrelerini boşalt satırı sıfırlayacaktır.

İkinci söz dizisi ise tekildir. Konum alıp değerini sıfırlar.

**Mesela**: 

.. code:: 

  değer Sayılar *tam = yeni(tam[20]);
  boşalt &Sayılar[2];

Bu örnekte ise yukarıdakinin aksine sadece 2 nolu hücredeki tam sayı boşaltılmıştır.

Konumu ve türü bilinen herşey sıfırlanabilir. 
Burada dikkat edilmesi gereken türün boyutu ve canlılığıdır. 
Canlı ayrılan kaynaklarda eğer ki ne kadar kaynak ayrıldığı biliniyorsa
sorun olmaz ama bilinmiyorsa ve işletim sistemi tarafından belirlenin alanın
dışına taşılmışsa işletim sistemi hata verir ve yazılımı 'SIGSEV' koduyla sonlandırır.

