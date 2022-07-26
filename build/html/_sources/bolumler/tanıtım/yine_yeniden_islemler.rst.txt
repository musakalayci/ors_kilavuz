Yine Yeniden İşlemler:
**********************

Tür ve birimler konusunu ele aldığımıza göre işlemleri irdelemeye devam edebiliriz. 

C dilinde en çok yaşanan sıkıntılardan birisi, önce türü tanımlayıp sonrasında 
o türle ilişkili işlemler tanımlanırken özellikle isimlendirme ve türün kendisini 
tekrar tekrar tanımlama konusunda yaşanan köle işidir. 

.. note::
  C'de bu tarz kıymıkların olmasının nedenlerinden birisi o dönemdeki 
  bilgisayarların kaynak yetersizliğinden ileri gelir. Mesela C'de 
  bolca 'strlen, fcntl' vb bir takım okunması, ezbenlenmesi anlanması 
  bile zor olan işlemler ve kütüphaneler var ve bunların amacı 
  sözlük algoritmasının işini kolaylaştırmaktan öte değil. 

  Yani özet olarak C'yi eleştirirken biraz dönemin koşullarını da 
  göz önününde bulundurmak gerekiyor.

Mesela dediniz ki:

.. code::

  struct dizi 
  {
    int hacim;
    int boyut;
    int* Icerik;
  }

Bu türe işlemler tanımlayacaksınız ama gördüğünüz gibi bu işlemler sadece 
**'int*'** dizisi için düzgün çalışacak ve bu da yetmezmiş gibi aşağıdaki gibi 
çirkinlikleri gözden çıkaracaksınız. 

.. code::

  void kütüphaneAdı_dizi_Topla(dizi* Dizi, int toplanacakSayı)
  {
    for(int i = 0; i < Dizi->boyut; i++)
      Dizi->Icerik[i] += toplanacakSayı;
  }

Şimdi beden kısmını boşverelim: 
İsim aslında içinde doğrusal bir ağaçlandırma yapıyor.
'kütüphaneAdı' + 
'işlemi anlam kümesine alan türün adı' + 'işlemin görevinin adı' gibi bir kalıba 
uyuyor. C'deki bu eksiklik çeşitli doğrusal kalıplarla aşılabilir. 
Daha ciddi sorun hem bu isim kalıplarının hem de onların bedenlerinin 
farklı yapıtaşları ve türler için tekrar edebiliyor olması. 

Mesela yukarıdaki diziyi, tam sayı dizisi değil de ondalık dizisi olarak yazsaydık 
ve bunların her bir elemanını bir ondalık ile toplayacak olsaydık yine aynı şeyleri tekrar edecektik. 

C'de bu sorunu öngeçişler ile fevkalede aşabiliriz 
ama bu sefer de derleyiciye türü tekrar tekar tanımlayacaktık. Dahası her bir öngeçiş işlemi çağrısı 
bizim kütüphanemizin boyutunu daha da şişirecekti ki bazen çok basit yazılımlar için ağaçlanan öngeçişler 
ürünü devasâ boyutlara ulaştırtabiliyor. 

Diğer taraftan bu konuyu çözmüş yazılım dilleri yok mu ? Tabi ki de var. Özellikle nesne 
tabanlı yazılım tarzının geliştirilme nedenlerinden bir tanesi bu yukarıda irdelediğimiz sorun ama 
sistem dillerinde nesne tabanlı tarz aşılması zor yapısal sorunlara yol açıyor ve daha içinden çıkılamazı 
hata ayıklamayı zorlaştırıyor. Bunlar yetmezmiş gibi işlemlerin cağrı yöntemini değiştire de biliyorlar;
ki sistem sürücüleri ile iletişime geçerken yeniden köprüler yazmanız, yazılımınızla 
sürücü arasında haberleşme sağlayacak arayüz geliştirmeniz gerekiyor. 
Nerede kaldı şimdi tasarım yapmanın keyfi ? Nerede bizim işimizi kolaylaştıran araçlar ? Yani her bir özelliği 
kullandığımda başımı nerede ağrıtacak öngöremiyorsam o özelliği kullanmanın ne anlamı var ?
Bu bir kabus.

Konu göründüğünden derin olduğu için Örs'ün bu konuda tüm dertlere devâ büyülü çözümler bulduğunu ileri sürmek 
hayalperestlik olur ama C iletişimini zorlaştırmadan, çağrı yöntemini değiştirmeden, türleri yozlaştırmadan da
yukarıdaki sorunları ele almak mümkün. 

Şimdi konuyu derinleştirebiliriz:

Tür İşlemleri:
^^^^^^^^^^^^^^
Yukarıdaki örnekte gösterildiği gibi tanımlı türlerin anlam kümelerinde yer alan işlemlerdir. 
C işlem çağrıları ile tam tutarlılığı vardır ve bu kaideyi bozmamak adına ilk değişkenleri pek çok yazılım 
dilinde olduğu gibi türün kendisidir. Mesela yukarıdaki C örneğini Örs'e çevirelim: 

.. code:: 

  tür dizi 
  {
    hacim   tam;
    boyut   tam; 
    İçerik *tam;
  }

  Dizi dizi 
  iş Yenile hacim tam 
  {
    Dizi.boyut  = 0;
    Dizi.hacim  = hacim;
    Dizi.İçerik = temiz(tam[boyut]);
  }

  Dizi *dizi 
  iş Topla toplanacakSayı tam 
  {
    her i:=0; i < Dizi->boyut; i++:
      Dizi->İçerik[i] += toplanacakSayı;
  }

  // çağrı örneği:
  iş Giriş argümanSayısı tam, _argümanlar **t8
  {
    değer tamDizisi dizi;
    dizi.Yenile(20);
    (&dizi).Topla(5);
  }

Baş kısmınında tanımlanan ilk değişken türün kendisi oluyor. Bu söz dizimi tanımlı işlemi türe bağlıyor. 
Fark edeceğiniz üzere türün derecesi var. Evet Örs dilinde tanımlı tür işlemlerinde ilk değişkenin tür kısmı 
önemli. Burada işlem bizden tanımlı türle yapılandırılmış 2 dereceli değer istiyorsa buna riayet edilmeli çünkü 
her ne kadar ilk değişken türe bağlıyor olsa da onun dışındaki davranışları herhangi bir diğer değişken ile **aynı**.

-------------

Nasıl türlere işlem bağlayabiliyorsak yalın türlere de aynı şekilde işlem bağlamak mümkün.


Sanal İşlemler:
^^^^^^^^^^^^^^^

Canlı işlem çağrısı yapmayan, türü illa ki belirli olmayan ve üretileceği zaman türü anlamlandırılan işlemlerdir.
C'deki işlevsel dengi öngeçiş işlemleridir denilebilir ama özlerinde farklıdırlar. Öngeçiş işlemleri çözümleme 
sürecinde anlamlandırılmışken sanal işlemler üretim sürecine kadar anlamlı değillerdir. Sanal çağrılarının 
yapıldığı satıra gelince türleri belirlenir ve çağrıldığı yere yamanırlar. 

İşlem çağırıları sanal olduğu için doğalarında hızlılardır ama derleme ürününün boyutunu artırırlar. 
Kullanım amaçlarından en önemlisi tekrar eden girdi çıktı işlemleridir. Bu işlemler özlerinde aynı şeyler olduklarından 
bunları mümkün olduğunca hızlı ve türlerini önemsemeden çağırmak isteriz. Bu örnek bir kaide olmamakla birlikte 
sanal işlemlerin uygulamadaki tasarım nedenlerinden bir tanesidir. 


Sanal Tür İşlemleri:
^^^^^^^^^^^^^^^^^^^^
Türlerle ilişkili bazı işler var ki bunların gerçek işlem olmasının anlamı bile yok. Mesela türlerin başlatılması, 
yenilenmesi, temizlenmesi gibi türler arası tekrar eden işlemler için canlı işlem çağrısı yapmayan, 
ilk türü hariç diğer türleri illa ki belirli olmayan ve üretileceği zaman anlamlandırılan işlemlere bu özel durumda ihtiyaç vardır. 
Mesela yukarıdaki örneği yeniden ele alalım: 

.. code:: 

  tür dizi 
  {
    hacim   tam;
    boyut   tam; 
    İçerik *tam;
  }

  Dizi dizi 
  sanal iş 
  Yapılandır hacim tam 
  {
    Dizi.boyut  = 0;
    Dizi.hacim  = hacim;
    Dizi.İçerik = temiz(tam[hacim]);
  }

  Dizi *dizi 
  iş Topla toplanacakSayı tam 
  {
    her i:=0; i < Dizi->boyut; i++:
      Dizi->İçerik[i] += toplanacakSayı;
  }

  // çağrı örneği:
  iş Giriş argümanSayısı tam, _argümanlar **t8
  {
    değer tamDizisi dizi;
    dizi.Yenile(20);
    (&tamDizisi).Topla(5);
  }

Burada **'Yapılandır'** işlemini sanal yaptık zira bu iş türü tekrar yapılandırmaktan başka bir görevi üstlenmiyor. 
Eğer ki sanal iş tanımlama özelliği olmasaydı **'Giriş'** işleminde değeri oluşturduktan, fark ederseniz başlatma
fiilini kullanmadım, sonraki satırlarda oluşturulan değeri yapılandıracaktı. 
Sanal türlerin yerinde kullanımına daha iyi örnek olamaz. Zira hızın bir önemi yok çünkü oluşturulan değeri zaten yapılandıracağız,
ürün boyutundaki artışın bir önemi yok yapılandırmak zorunada olduğumuz için türün boyutu artacak. 
Özet olarak hız ve hafıza arasındaki
ters orantı tahteravallisine binmeden bu sorunu okunabilir bir şekilde hallettik ki sanal türlerin uygulamadaki tasarım amaçlarından 
en önemlisi budur. Mesela şunu da yapabilir miydik ? 

.. code::

  /*yukarıdaki örneği tekrar ele alalım*/
  ...
  sanal iş 
  Dizi hacim tam : dönüş dizi 
  {
    dönüş.boyut  = 0;
    dönüş.hacim  = hacim; 
    dönüş.İçerik = temiz(tam[hacim]);
  }
  ...
  iş Giriş argümanSayısı tam, _argümanlar **t8
  {
    tamDizisi := Dizi(20);
    (&tamDizisi).Topla(5);
  }

Bu örnekte tanımlı **'Dizi'** işi sanal ama türe bağlı değil ve 
bize yapılandırılmış birinci dereceden dizi değeri dönüyor. 
Tahteravallide değiliz, temiz ve okunabilir kod. 

Yalın Tür Sanal İşlemleri:
^^^^^^^^^^^^^^^^^^^^^^^^^^
Yalın türlerin amaçlarından en önemlisi onlara tür bağlayabilmektir. En basitinden 
posix kütüphanesindeki işlemlerin çoğu **'int'**, Örs dengi **'tam'**, yapıtaşıyla işlem yapar 
ama bu yapıtaşlarının kendi görev alanlarında anlam kümeleri vardır. 
Bazen bu tam sayı hata anlamı taşırken, 
bazen açılan belge anlamını ve başka başka anlamları taşır. 

Yalın türlerde sanal işlemler ile tüm bu anlam kargaşasının önüne geçebilir ve aynı yapıtaşlarının 
kullandığı gibi görünen ama özlerinde farklı olan işler tasarlayıp kavramlar arası çizgiyi belirginleştirebiliriz. 
Bu kavram sınırları önemli mesela elinizde **'rgba'** renk türü vardır ve bu tür aynı anda hem 
resimlerde, hem oyunlarda farklı kavram alanlarında kullanılabilir. Tür aynı ama görevleri farklı.

Mesela:

.. code:: 

  tür belge tam;

  öz belge
  sanal iş 
  Aç _konum *t8, izinler tam, mod tam : tam
  {
    öz = sys::open(_konum, 
      izinler, 
      mod); 
    eğer öz < 0: 
    {
      durum error::no:
      {
        seçim error::code::Access:
          stdio::printf("Erişim hatası\n");
        varsayılan:
          stdio::printf("bilinmeyen hata : %d.\n", öz);
      }
    }
    dön öz;
  }

Yukarıda meşhur **'open'** işleminin döneceği **'tam'** 
türü belge olarak yalın halde tanımlanmış ve kavram alanında olası hatayı ele alan yeni bir işlem tasarlanmış.
Bu görevi belge türündeki değerin oluşturulduğu yerde de yerine getirebilirdik ama burada aynı tür için olası 
tekrar eden sıralı satırlar kümesi var. Bir diğer deyişle sanal işlem kullanımı için mükemmel bir örnek.  

----------

Kalıp Sanal işlemler:
---------------------

Nasıl gerçek olmayan, özlerinde sanal türler olan kalıplar var ise bunlara bağlanabilecek sanal işler de vardır. 
Kalıpların türü belirgin olmadığı için işlem tanımlayamayız ama zaten kalıplar uygulamadaki güçlerini buradan alıyor. 

Yukarıdaki örnekte eğer ki **'tam'** dizisi değil de ondalık dizi ya da istenilen türde bir dizi tanımlayıp 
işlemleri kullanmak isteseydik bunu yapamayacak olduğumuz gibi tekrar tanımlamak zorunda kalırdık. Tekrar aynı şeyi 
bu kadar temel bir algoritma ve tür için yazmanın anlamı yok. Örneği kalıpları kullanarak yeniden ele alalım 

.. code:: 

  kalıp dizi x 
  {
    hacim   tam;
    boyut   tam; 
    İçerik *x;
  }

  Dizi dizi'x 
  sanal iş 
  Yapılandır hacim tam 
  {
    Dizi.hacim  = hacim;
    Dizi.boyut  = 0;    
    Dizi.İçerik = temiz(%*Dizi.Öğe[hacim]); 
    //% işlemiyle tür alıyoruz ki tür belirlendiğinde hesabı tutulabilsin.
  }

  Dizi dizi'x 
  sanal iş 
  Topla toplanacakSayı x 
  {
    her i:=0; i < Dizi->boyut; i++:
      Dizi->İçerik[i] += toplanacakSayı;
  }

  // çağrı örneği:
  iş Giriş argümanSayısı tam, _argümanlar **t8
  {
    değer tamDizisi dizi'ondalık;
    dizi.Yapılandır(20);
    tamDizisi.Topla(5.0);
  }


Özellikle bu konunun **'dizi'** kalıbıyla anlatmayı seçtim zira bu kalıp o kadar temel ve o kadar çok kullanılan 
bir kalıp ki C'de ne kadar çok dizilerle ilgili aynı işlemi yazdım sayısını unuttum.

