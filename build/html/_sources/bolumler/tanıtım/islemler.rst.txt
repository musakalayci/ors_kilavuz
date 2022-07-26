********
İşlemler
********

Eğer belirgin bir görevi yerine getiren satır kümesi var ise 
bu satır kümesine mantıken işlem denilebilir.

Örs dilinde işlemler sıralı satır kümesi olarak tanımlanır. 
Haskell, Ocaml vb. dillerin aksine Örs, C, C++ işlevsel değil; sıralı bir dildir. 
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

  **Sade işlemler:**
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
    okunurluğu sade ve kolay kılmaktır. 



  **Değişkenler:**
    İşlemlerin girdileri ve çıktıları olabilir. 

    .. note::
      Örs veyâ diğer sıralı dillerdeki değişkenler kavramı
      matematikteki bağımlı ve bağımsız değişkenlerle karıştırılmamalıdır. 
      Sıralı diller makinaya yakın olduğu için; üretilmiş makina kodu 
      işletim sisteminin işlem yığınına alınacak ve bu aşamada matematikteki 
      kavramlar yozlaşmaya uğruyor. O yüzden **değişkenler** kavramını kendi 
      içerisinde ele almak daha sağlıklı.
    
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
    Diyelim sadece iki değişken 
    kabul etseydi o zaman **türleri** kullanarak dilediğimiz kadar değişkeni tek seferde bile işlemek mümkün olurdu.
    Bu nedenden ötürü burada önemli olan değişken tanımlarında bir üst sınır olduğudur. 
    Zira ben bu güne kadar 16 değişkeni olan bir işlem görmedim. 

    **Çıktılar:**
      Yukarıdaki 'Topla' işlemine küçük bir değişiklik yapalım: 

      .. code:: 

        iş Topla a tam, b tam; dönüş tam:
          dön a + b;


      Derleyiciye emredilen yine değişmedi ama Örs dilinde çıktılara isimlendirdiğimiz sürece erişebiliriz. 
      Bu **go** ve benzeri dillerin bizimle tanıştırdığı harika bir özellik. İşlemler içerisinde pek çok sefer
      döneceğimiz değeri tanımlamak zorunda kalıyoruz. Gerek bile yok. Çıktısı olan işlemlerde 
      zaten dönülecek türün hafızası önceden ayrılıyor ve tekrar başka bir dönüş değeri tanımladığımızda iyileştirme aşamasında 
      doğal olarak siliniyor çünkü gereksiz bir değer.

      .. code:: 

        iş Topla a tam, b tam; dönüş tam:
        {
          dönüş = a + b;
        }

        /*ya da tek satırlık tanımla*/ 

        iş Topla a tam, b tam; dönüş tam: 
          dönüş = a + b; 

-----------------

İşlem baş kısmı özet olarak yukarıdaki gibidir. 
Örs dilinde işlemler tanımlanırken 'iş' sözcüğü kullanılarak başlanır.
Sonrasında işin birim hafızasındaki benzersiz adı verilir, 
eğer varsa değişkenler aralarına virgül konularak tanımlanır 
ve eğer varsa çıktı kısmı girdilerden ayırmak için çift nokta ile ayrılır  
ve son olarak ise satırı tanımlanır. 
Makina dili yapılanması 
C dilinin derlendiği işletim sistemleri için belirlediği standartlara uyar. 

İskelet: 
^^^^^^^^
    **Hazırlanıyor.**

Beden kısmına ise her biri sıralı ifadelerin kümesi olan satırların olduğu sıralı küme satırı kabul eder. 

İşlemler konusunu irdelemeyi **türler** ve **birimler** konularını ele alana kadar burada bırakmak zorundayız.








