Döngü Satırları 
***************


Bilgisayar belleğinin aslında devasa bir dizi olduğu düşünülünce, bu dizinin 'a'
noktasından 'b' noktasına gitmeyi istemek kadar temel bir istek olamaz. Tam olarak  
bu amacı yerine getirmek için Örs dili çeşitli döngü yöntemleri kullanmaktadır. 

Döngülerin amacı verili kod dizisini koşul sağlanmayana kadar tekrar tekrar 
işletmektir. Bu yönüyle motorlara benzerler. En basitinden siz arabayı çalıştırdınız ve
arabanın motoru dönmeye başlar ve öyle devam eder ta ki siz motoru kapayıncaya kadar ya da 
yakıt bitinceye kadar. Yani siz koşulu sağlamayana kadar o motor çalışmaya devam eder. 

Burada dikkat edilmesi gereken husus Örs dilinin C dilinden daha fazla yönlendirmeler 
tanımlaması ve döngüler üzerinde daha fazla denetim sağlamasıdır. Yönlendirmeler konusuna 
ayrı bir başlık açacağız. 


.. glossary::

   Her Döngüsü: 

      .. code::

         iş ArgumanlarÖrneği 
            argumanSayisi   tam,
            _argumanlar   **t8: tam 
         {
            // ilk döngü
            //argümanları dizi erişimiyle yazdır.
            her değer i tam = 0; i < argumanSayisi; i++:
               stdio::printf("-> %s\n", _argumanlar[i]); 
            
            //ikinci döngü:
            //argümanları konumlarından yazdır.
            her değer t **t8 = _argumanlar; *t; t++:
               stdio::printf("=> %s\n", *t); 
         }

    
      Yukarıdaki örneğin ilk 4 satırını göz ardı edecek olursak, bu işlem basitçe, 
      önce yazılım argümanlarını dizi erişimi ile daha sonra konum erişimiyle yazdırıyor.  

      'Her' sözcüğü ile başlayan satır içerisindeki ilk satırda değer ya da değerler tanımlanır. 
      Sonrasındaki satırda koşul belirtilir, üçüncü satırda ise tanımlı değerler güncellenir ve her 
      döngüsünün beden satırına geçilir. 

      Bu kısmı tabî ki de sadece bir söz dizimi. Hepimizin C dilinden eline yapışmış alışkanlık. 
      Bu satırların anlam sıralaması farklı olsaydı yani ilkin güncelleyip, sonra koşulu değerlendiremezmiydik ? 
      Tabi ki de değerlendirebiliriz ama mesele o değil. Örs dili makina diline dönüştüğünde, biz tasarımcılar olarak 
      istiyoruz ki derleyicinin ürettiği kod C derleyicisinin ürettiği kod ile bire bir eşdeğer olsun. 
      Yani her döngüsünü yukarıdaki gibi tanımladığınızda, üretilen makina kodu ile C derleyicisinin ürettiği
      makina kodu tıpa tıp aynı. 

      Diğer taraftan tam burada basit bir okuma sorunu ortaya çıkıyor. Özellikle internet, oyun, 
      arayüz uygulamalarında çoğu zaman döngüyü koşullarla değil sayaçlarla yönlendiriyoruz ve 4 satırlık her döngüsü 
      okurken göze batıyor. Bir diğer konu ise yukarıdaki söz dizimi makina dili üretirken de 5 satır kod üretiyor. 
      
         C tarzı  döngü:  

         .. code:: 

            her ; ; güncellemeYapacakİşlem(): 
            { 
               işletilecekBeden(); 
            }
            /*
               Burası ise devam satırı.
            */ 

      Şimdi bu döngü satırına basitçe bir ameliyat yapalım. Değer tanımlanması gereken kısımda değer tanımlanmamış. Yani boş satır var. 
      Koşul satırı yine boş. Güncelleme satırında bir işlem çağırılmış ve bu üretilecek ilk makina dili satırı. 
      Beden kısmında da dolu satır var ve bu da bizim ikinci makina dili satırımız. 

      Ama, fakat, lakin o yorumun olduğu yerde bir diğer satır daha var. Devam satırı. 
      Makina kodunda devam ederken nereye devam edeceğini söylemen gerekiyor. Örs, C, C++ dillerinde devam satırını 
      siz tabi ki de yazmıyorsunuz ama makina dilinde o satır var ve yukarıdaki döngünün makina dilinde, yani özünde, 
      3 satırı var. 

      Peki ama biz işlemci değiliz ki bize ne bundan ? Çok doğru ama biz bu kodu okuyacak olanız. 
      5 satır tanımlayıp, 3 satır ürettirmenin anlamı yok. Yani argümanlar örneğindeki gibi 4 
      satırlık döngü tanımladığınızda aslında makina 5 satır kod görecek. 
      Bu örnekte ise tanım ve koşul kısmı boş satır ve derleyici hiçbir makina kodu üretmeyecek. 

      Peki öyleyse fazladan iki satırı tanımlamanın ne anlamı var ? Burada basit bir görsel soyutlama yapmamız ve her döngüsünün 
      söz dizimini kıvraklaştırmamız gerekiyor. 

   Her döngüsü söz dizimi çeşitleri:

      .. glossary:: 

         Sonsuz döngü: 

            .. code::    

               her: 
                  herhangiİşlem(); 
            
            Yukarıdaki örnekte görsel uygulamalarda, veri arz uygulamalarında bolca kullanılan bir sonsuz döngü örneği var. 
            Sadece beden satırında bir takım işlemler çağırılmış. 
            Derleyici 1 satır görecek ve 2 makina satırı üretecek. 

            Göze sade görünüyor. Derleyiciye sade görünüyor ve makina zaten sade görecek. 

         Tanımsız döngü:
         
            .. code::

               her devamMı(); güncellemeYap(): 
                  bedenKısmı(); 
            
            Fark ettiyseniz değer tanımlaması beklenen satır yok. Zaten iş yaparken çoğu zaman değerler önceki 
            satırlarda tanımlanmış olacak. 
            'her' satırı içinde 2 satır tanımlı. Sırasıyla ilk kısım koşul satırı ve bu kısmın koşul olması bir kaide. 
            İkinci satırda güncelleme kısmı var, sonrasında ise beden satırı ve gizli son satır. Derleyici 
            Üç satır görecek ve dört satır üretecek. 

            Göze sade görünüyor. Derleyiciye sade görünüyor ve makina zaten sade görecek. 

            not: 
               şunu da eklemek isterim, ilk satırda değer tanımlanması sadece bekleniyor. İllaki değer tanımlayacaksınız 
               diye bir kaide yok. 
         
         Koşullu döngü: 

            .. code:: 
               
               değer i tam = 0;
               her i < 10:
               {
                  stdio::printf("-> %d", i);
                  i++; 
                  /*i'yi güncellemek tamamen isteğe bağlı.*/
               }
            
            Yazılıma başladığınızda ilk göreceğiniz döngü örneği. Görüldüğü üzere 'her' sözcüğünden sonra 
            koşul var ve bu Örs derleyicisi için şu anlama geliyor: 'i' değeri ondan küçükken döngü bedeni çalıştırılacak ve 
            güncelleme döngü bedeni içerisinde halledilecek ya da halledilmeyecek. 

            C dilindeki 'while' döngüsü ile bire bir aynı kod Örs derleyicisi tarafından üretilecek. 
         
    
   Tüm döngüsü: 

      .. code:: 

         değer i tam = 0;
         tüm i < 10:
         {
            stdio::printf("-> %d", i);
            i++; 
            /*i'yi güncellemek tamamen isteğe bağlı.*/
         }

     Fark ettiğiniz üzere yukarıdaki koşullu her döngüsü ile bire bir aynı. Ama 'tüm' 
     döngü satırının çeşidi yok. C dilindeki 'while' döngüsüne karşılık gelen sade bir döngü satırı. 

     Tüm döngüsü için 2 satır istenecek ve sonuç olarak 3 satır makina kodu üretilecek. 
   
   Sonuç: 

      'her' sözcüğünü döngü satırı tanımlarken seçmemizin amacı türkçede akla yatkın olması. 
      Türkçenin benzersiz matematiksel doğası var. 
      
      Mesela aşağıdaki satırı Türkçeye çevirmeye çalışalım: 

      .. code:: 

         her değer i tam = 10; i > 0; i--: 
         {
            birşeyler();
         }

      'i' değerini 10'a eşitleyip; her bir 'i' ondan küçük iken; 'i' değerini azaltarak 'birşeyler' işlemini çalıştır. 

      Eğer burada söz dizimine odaklanmazsanız ilginç bir ayrıntıyı yakalayabilirsiniz. Türkçede 
      diğer pek çok dilin aksine söz dizimi kuralı yok ve bu durum Türkçeye kıvraklık, ifade yeteneği 
      ve güç katıyor. Yukarıdaki döngü satırını bu denli insan diline bire bir çevireceğiniz ve iyelik ekine kadar makinaya
      anlatabileceğiniz nadir dillerden bir tanesi Türkçe. 

      O yüzden 'her' sözcüğünü döngü satırlarını tanımlarken seçtim. Peki her sözcüğünü seçmeseydin ? 
      Tabi ki de özünde hiç bir önemi yok. İsteserseniz kendi tasarladığınız dilde 124323 sayısını döngü satırları
      tanımlamak için bile kullanabilirsiniz. 

      Basitçe tekrar söylemem gerekirse: "Okuduğumuz kodun, derleyicinin okuduğu kodun ve üretilen kodun olabildiğince örtüşmesini sağlamak."

      Peki buradaki döngü satırlarının makina kodu üretimi konuları diğer yazılım dillerinde öyle değil mi ? 

      Bazen öyle, bazen değil ve özellikle üretilen kodun iyileştirilme aşamasında boş ya da gereksiz satırlar silinecek. 

      Burada bu tanımı yapmaktaki amaç
      gözümüzün gördüğü kod ile Örs'ün ürettiği kodun olabildiğince örtüşmesi ve 
      bunun bir kaide olarak belirtilmesi. Yani diyelim ki Örs onuncu sürümünü yayınladı, 
      bu kaideler değişmeyecek ve bizler nasıl kod üretiyor diye endişelenmeyeceğiz. 

      Altı çizilmesi gereken diğer konu ise üretilen kodun mümkün olduğunca C dili ile uyumlu olması. Konu döngüler olunca 
      bu istek önemsiz durabilir; en nihayetinde işlem çağrıları dışında 
      üretilen kodun diğer kütüphanelerle iletişimi pek olmuyor 
      ama tepeden tırnağa C dili ile uyum sağlamak Örs'ün tasarım amaçlarından bir tanesi. 
      Tasarımın merkezi kaidelerinden biri bu ve işletim sistemi kütüphaneleri ile rahat rahat iletişim kurabilmek için bu 
      kaideyi tepeden tırnağa bozmayacağız. 


