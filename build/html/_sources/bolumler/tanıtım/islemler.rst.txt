İşlemler
********

Eğer belirgin bir görevi yerine getiren satır kümesi var ise 
bu satır kümesine mantıken işlem denilebilir.

Örs dilinde işlemler sıralı satır kümesi olarak tanımlanır. 
Haskell, Ocaml vb. dillerin aksine Örs, C, C++ işlemsel değil; sıralı yani işlevsel bir dildir. 
Tasarım, Örs işlemlerinin görevi ve işlevi olduğunu varsayar. 
Bu konuda yanlış anlaşılmamak gerçekten önemli. Zira yeni öğrenenler 
sıralı dillerdeki işlem kavramının matematikteki işlem kavramı olduğunu ister istemez 
düşünüyor. Oysa bilgisayara matematik işlemini tanıtmakla işlevi yerine getirmek bambaşka konular. 
Yani Örs bire bir lambda matematiği ile örtüşmez. Bunun tasarım nedenleri başlı başına 
ayrı bir konu ve burada bizi ilgilendiren kavram Örs ve 
diğer benzeri sistem dillerinde işlemlerin ele alınışının 
matematikteki işlem (fonksiyon) kavramı ile aynı olmadığıdır. 


İşlemler Örs dilinde satır değildir ama beden olarak satır bekler. 

.. glossary:: 
  Sade işlemler:
    Girdisi ve çıktısı olmayan işlemlere sade işlemler Örs dilinde aşağıdaki gibi tanımlanır. 

    .. code:: 

      iş Merhaba:
      { 
        stdio::printf("Merhaba Dünya !");
      } 

    Örnekte görüldüğü üzere; 
    işlemler tanımlanırken 'iş' sözcüğü kullanılarak başlanır. 
    Sonrasında işin derleme birimindeki benzersiz adı verilir ve son olarak ise beden satırı tanımlanır. 

    Kısa yol olarak tek satırlık işlemler de aşağıdaki gibi tanımlanabilir. 

    .. code:: 

      iş Merhaba:
        stdio::printf("Merhaba Dünya !");

      /*ya da*/

      iş DöngülüMerhaba: 
        her değer i tam = 0; i < 10; i++: 
          stdio::printf("Merhaba Dünya !");
      

    Bu örnekte sadece tek satırlı işler tanımlayabilme yeteneğindeki amaç
    okunmayı kolay ve sade kılmaktır. 

  Değişkenler:

    İşlemlerin girdileri ve çıktıları olabilir. 
    
    .. code:: 
      
      iş Topla a tam, b tam; tam:  
      {
        dön a + b;
      }

    Derleyiciye bu işlemin baş kısmıyla denilen şey basitçe: 
    "a ve b tam sayı değişkenleri kabul edip, tam sayı dönen 'Topla' işini tanımla."
  
    Değişkenler tanımlı işin beden satırında değer gibi ele alınsalar da; hem derleyici tarafından 
    yorumlanması hem de bilgisayarda işlenmesi bakımından özlerinde değerlerden farklılardır. 

    On altı farklı girdi değişkeni ve tek bir çıktı değişkeni tanımlanabilir. 

    Burada değişken sayısının üst sınırının 16 olmasının nedeni basitçe uygunluğudur. 
    Bildiğim kadarı ile GNU C dilinde 255 farklı değişken tanımlanabiliyor ama Clang derleyicisi farklı ele alıyor olabilir. 
    Burada önemli olan değişken tanımlarında bir üst sınır olduğudur. 
    Zira ben bu güne kadar 16 değişkeni olan bir işlem görmedim. 

    .. glossary::

      Çıktılar: 

        Yukarıdaki 'Topla' işlemine küçük bir değişiklik yapalım: 

        .. code:: 

          iş Topla a tam, b tam; dönüş tam:
            dön a + b;


        Derleyiciye emredilen yine değişmedi ama Örs dilinde çıktılara isimlendirdiğimiz sürece erişebiliriz. 
        
        ... code:: 

          iş Topla a tam, b tam; dönüş tam:
          {
            dönüş = a + b;
          }

          /*ya da tek satırlık tanımla*/ 

          iş Topla a tam, b tam; dönüş tam: 
            dönüş = a + b; 
        

    Özet olarak; Örs dilinde işlemler tanımlanırken 'iş' sözcüğü kullanılarak başlanır.
    Sonrasında işin birim hafızasındaki benzersiz adı verilir, 
    eğer varsa değişkenler aralarına virgül konularak tanımlanır 
    ve eğer varsa çıktı kısmı girdilerden ayırmak için çift nokta ile ayrılır  
    ve son olarak ise satırı tanımlanır. 

  İskelet: 
    **Hazırlanıyor.**






