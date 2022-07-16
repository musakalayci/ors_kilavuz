*******************
Konumlar ve Diziler 
*******************

Sistem dillerinin en çetrefilli ama eğlenceli konusu: Konumlar. 

Basitçe hayal edelim; Bir bakkal deposu var ve burada sayılamayacak kadar çok kutu ve 
içinde de bir takım abur cuburlar var. Tüm bu kutular numaralanmış ve numaralanmış 
raflara yerleştirilmiş. Kim yerleştirdi bilmiyoruz da umursamıyoruz da. Amacımız 
bir an önce 'çuklatalara' erişmek. İşin güzel yanı laz bakkal bize demiş ki 
\"Al üzerinde 'LB 22 543' yazan bu kağıdı takip et, 
dilediğin kadar çuklataya yumul gitsin.\"

Ben olsam, kağıttaki bilgiyi yorumlamakla başlardım. Derdim ki, 
\"Tamam LB laz bakkal demek ve zaten depodayız,
22 ve 543 ise ya raf ya da kutu numarası olamalı. 
İlkin 22 numaralı rafla başlayayım uymazsa tersini denerim.\"
Basit bir strateji ve elimde bir kutu çuklata var. 

Konumlar kunusu da bu örneğe benziyor. Konu çetrefilli çünkü 
konumların gösterdiği yerlerde çuklata yok yine bir diğer sayı var. Eğlenceli 
çünkü o sayı her anlama gelebilir. 
Mesela veri tabanındaki en sevdiğimiz çuklata kutusunun depodaki konumunu verebilir 
ya da o konumda komik vidyo adresi olabilir yani herşey olabilir. 
Örs dilinde tabi ki de konumlar diye bir özellik yok; 
hatta diğer sistem dillerinde de yok ama kavram hem sanal dünyada hem de gerçek dünyada 
temel bir konu olarak yer aldığı gibi Örs'de dahil tüm sistem dillerinde yer alıyor.

Sadece Örs değil diğer sistem dillerinde de konum kavramı bir soyutlamadır. 
Özlerinde mimari boyutunda doğal sayılardır.
Mesela 64 bitlik işlemcideki konumlar da 64 bit genişliğindedir ve bu konumlar basitçe bilgisayar
hafızasındaki 64 bitlik hücrelerin numaralarıdır. 

Düz mantıkla bilgisayar belleği uç uca dizilmiş boncuklar dizisi gibi düşünülebilir. Mesela 
benim 64 bitlik bilgisayarın 8gb hafızası var ve bu **düz mantıkla** 0'dan (8gb/8)'e kadar 
numaralanmış 8 bitlik boncuklar var ve benim öyle bir kavrama ihtiyacım var ki ihtiyaç halinde 
bu boncuklara ulaşıp içindekini alayım.

Bu kavram konumlar oluyor. Bir önceki **düz mantık** örnekte gerçek konumlar var. 
Yukarıdaki Laz Bakkal örneğinin aksine elimizde doğrudan değeri gösteren doğrusal konum var. 
Gerçekte olan şey ise daha karmaşık. 
İşletim sistemi belleği bölgelere ayırıyor ve bu bölgeleri işlemler ihtiyaç duyduğunda onlara atıyor. 
Yani siz bir konumda bulunan değere ulaşmak istediğinizde önce işletim sisteminin yazılımıza atadığı bölgeye,
sonra değere ulaşıyorsunuz ve bu ucu açık kavrama sanal konum deniyor ki yukarıdaki Laz Bakkal örneğinde, 
elimizdeki kağıtta yazan konum sanal bir konum.

Örs konumlar konusunu C dilindeki gibi ve Java, C#, OCaml gibi dillerin aksine, yorumsuz ele alır. 
Zira zaten işletim sistemi sanal konum vereceği için bunun üzerine bir algoritma daha eklemek 
yazılımın hızını azaltır. Böylece işletim sisteminin bize ayırdığı bölüme doğrudan erişim sağlanabilir. 
Bu kulağa hoş gelse de aynı zamanda olabildiğince tehlikelidirde. 
Diğer taraftan konumları yorumlamadan ele almak
Örs'ün tasarım ilkeleriyle de çelişmez. Örs'ün tasarım felsefesi bu ve benzeri olaylara
\"eğer bir hata verilecekse bırakalım verilsin\" yargısıyla yaklaşır. 
Çünkü konumlarla ilgili hatalar konumların doğrudan erişim 
yeteneğinden ziyade, hafıza yetersizliği, sıralama yanlışlığı, 
atanan bölge dışına taşma, boş konum ve benzeri sorunlardan kaynaklanır
ve benzeri hatalar yazılımın hata ayıklama sürecinde engellenebilir ki 
yukarıdaki yargının atıfta bulunduğu anlam da budur. 
Bu yönüyle konumlarla ilgili olası tehlikeler yazılımcının sorumluluğundadır ve 
ne işletim sisteminin ne de sistem dillerinin sorumluluğunda değildir. 

Örs dilinde ve diğer sistem dillerinde konumlar **'mimari'** 
bayt genişliğinde yapıtaşlarıdır. Bu özelliğe atıfta bulunmak 
**'şey'** yapıtaşının kavramsal görevlerinden de bir tanesidir. 

Örs konumları kullanmak için C söz dizisinden yararlanır. 

.. code:: 

  iş KonumÖrneği 
  {
    değer a t64 = 0x0_47_46_45_44_43_42_41;
    değer K *t64 = &a; // a'nın konumunu K'ye geçiriyoruz.
    stdio::printf(
      "a: 0x%llx\n" 
      "a'nın konumu: %p\n"
      "K: 0x%llx\n"
      "K'nın konumu: %p\n",
      a, // a değeri 
      &a, // a'nın konumunun alındığı ifade 
      *K, // K'deki konuma gidildiği ifade
      K); // ve K değerindeki konum.
  }

Tabi ki de böyle bir örneği gerçek hayatta pek kullanmazsınız. 
İşte tam burada bir kavramı sizinle tanıştırmam gerekiyor: Dereceler.

---------------

Konum Dereceleri:
^^^^^^^^^^^^^^^^^

.. code:: 

  iş Giriş 
  argümanSayisi   tam,
  _argümanlar   **t8
  {
    //argümanları konumlarından yazdır.
    her Argüman := _argümanlar; *Argüman; Argüman++:
      stdio::printf(
        "=> konum değeri: %p, konumdaki değer: %s\n", 
         Argüman, 
        *Argüman); 
  }

Yukarıda ise **'_argümanlar'** değişkeninde harfler 
dizisinin dizisinin konumu **Giriş** işlemine verilmiş. 

Örnekte görüldüğü üzere **'_argümanlar'**' değişkeninin türünde iki yıldız var. 
Derece dediğimize göre şunu diyebilir miyiz : \"**'_argümanlar'** değişkeni iki derecelidir\" ?
Malesef hayır. Değerin yaşadığı konumu saymayı unuturuz. Yani aslında 
**'_argümanlar'** değişkeni 3 dereceli bir değer. Çünkü tüm değişkenler aynı zamanda 
birer değer. 
Tanımladığınız tüm değerlere ve işlemlere atıfta bulunulurken, 
onların fiziki konumlarındaki veri işlem yığınına konulacak. 
Özet olarak değerlere olan herbir atfınız için 
konuma gidip derecesini düşürüp veriye 
öylece erişiliyor.  

Bu manada birinci dereceden değerler tüm tanımlı değerler oluyor. 
Ayrıca, konum boyutu arttıkça derecesi de artıyor. 

Burada elimizde kendi kendini gösteren kavram var. 
Biraz kafa karıştırıcı olsa da iletişim kuramının çıkmaz 
sokaklarında sıklıkla bu tarz varlıklara rastlanır.

Bu kavramı tanımlama gereği duydum zira hem derleyicide kullanılıyor, 
hem llvm altyapısında,
hem de siz aslında farkında olmadan zihninizde zaten o şekilde canlandırıyorsunuz. 
Diğer taraftan, kavramı tanımlamak bizi dizinin dizinin disinin dizinin 
konumu gibi çirkin anlatım kullanmaktan koruyacak.

Peki derecesi olmayan değer olabilir mi ? Tabi ki de hayır. 
Derecesi yoksa yaşadığı konum da yoktur ve yani o değer yoktur. 
Olmayan bir değerin derecesi olabilir mi ? Hayır.

Diyelim ki **'_argümanlar'** değerine '\*\*_argümanlar' ifadesi ile atıfta bulundunuz.
İlkin **'_argümanlar'**'ın yaşadığı konuma, sonra orada tutulan konumdaki diziye, 
sonra ise dizinin ilk harfine gideceksiniz.

Örneğe tekrar dönelim: Elimizde 3 dereceli değer var. 
Yani bir dizi konumu var ve o konumda diğer dizilere olan konumlar tutuluyor.
Peki ben bir derece indirsem yani **'_argümanlar'** değerinin yaşadığı yere gitsem 
ve bunu farklı bir değere atayıp konumunu artırarak içteki 2 
dereceli dizileri yazdıra bilir miyim ? 
Evet ve yukarıdaki örnek tam olarak bunu yapıyor. 

.. note:: 

  Tekrar tekrar belirtmek isterim: Tüm değerler zaten bir hafızadaki bir konumda yaşıyor. 
  Çoğul dereceli değerlerle o konumları her hangi bir değer ile saklayabiliyoruz. 

Fark edeceğiniz üzere konumlar ve diziler birbirleri ile bir şekilde ilişkili ama 
sanki ilişkiyi kuracak kavramı bilmiyoruz ki konum kavramının ve dizilerin birbirlerine karıştırılmasında 
yatan ana nedenlerden birisi. Konumlar bir kavram. Konumlarla ilgili gerçek olan tek veri 
özlerinde doğal sayı değerleri olması ama diziler ise yazılımda en az d64 yapıtaşı kadar gerçek 
bir veri türü. 

Diziler: 
^^^^^^^^

Hafızada sıralı ve ardışık yer alan üyelerinin bir önemi olmaksızın
doğrusal veri yapısına sahip temel türe denilir. 

.. code::

  iş DiziÖrneği 
  {
    stdio::print("\nDizi Örneği:\n");
    değer tekBoyutlu t8[8] = 
      [65, 66, 67, 68, 69, 70, 71, 0];
    değer ikiBoyutlu t8[4,2] = 
      [[65, 66], 
       [67, 68], 
       [69, 70], 
       [71, 0]];
    değer üçBoyutlu  t8[2, 2, 2] = 
      [[[65, 66], [67, 68]], 
       [[69, 70], [71, 0]]];
    stdio::print("-> '%s'\n-> '%s'\n-> '%s'\n",
      &tekBoyutlu[0],
      &ikiBoyutlu[0,0],
      &üçBoyutlu[0,0,0]);
  }

Örnekte yapılan şey gayet basit, 
**'tekBoyutlu'** dizisi için **(@tam)\*8** kadar;
**'ikiBoyutlu'** dizisi için **(@tam)\*4\*2** kadar;
**'üçBoyutlu'** dizisi için **(@tam)\*2\*2\*2** kadar bayt hafızası
üretim sürecinde ayrılıyor ve dizinin her bir üyesinin içine belirtilen değerler yazılıyor.
Arayüzdeki çıktıdan anlayabiliriz ki; hafızada yaşadıkları konum farklı olsa da konumlardaki veri aynı 
ama tür ifadeleri kullanılarak aynı veri derleyiciye farklı yorumlatılmış.  
Çünkü üç farklı konumda yaşayan dizinin üçünün de tür bayt genişliği ve sıralaması aynı 
ve hafızada 32 bayt yer kaplıyor. 

C söz dizisinin aksine Örs'de dizi tür ifadesinin sözdizisi farklıdır. 
C'de yukarıdaki **'üçBoyutlu'** dizisini tanımlamak için **'[2][2][2]'** 
sözdizisini kullanırken; Örs için **'[2, 2, 2]'** sözdizisini kullanıyoruz. 
Nedeni ise yazarken virgül koymanın ele daha yatkın olması. 

Peki yukarıdaki **'tekBoyutlu'** dizisinin derecesi kaç ? İki mi ? Külliyen hayır. 
Orada tek dereceli değer var. 
Bu değerin içinde sıralı birden fazla değerin olması derecesini arttırmıyor ve 
konumlar kavramı ile dizi türünün biz tasarımcıların kafasını karıştırıyor. 
Çünkü işletim sisteminden hafıza alanı istediğimizde onu dizi gibi yorumlayabiliyoruz ve 
onu en az iki dereceli değerle saklayabiliyoruz. Diğer taraftan diziler ise tek dereceli. Bu nasıl olur ?

Şöyle ki: Varsayalım ki işletim sisteminden doğrusal hafıza alanı istediniz. İşletim sistemi size 
tek dereceli değeri verdi ve onu yine tek dereceli konuma sakladınız; etti iki dereceli konum değeri. 
Tanımladığınız dizinin ise yaşadığı hafıza alanının yine bir önceki gibi doğrusal olduğunu varsayalım. 
Zaten doğrusal bir hafıza alanında tek dereceli olarak tanımlı ve bir değerde saklı; etti bir dereceli dizi değeri. 

Anlamsız geliyor olabilir. Bu ayrım o kadar temel ki beyinde oturması yıllar alıyor. 
Bu manada sizlerle bir diğer hayati kavramı daha tanıştırmalıyım: 

---------------

Boyutlar:
^^^^^^^^^
Geometrideki ya da doğrusal cebirdeki boyut kavramının yazılıma izdüşümü denilebilir 
ama aynısı denemez. 
Mesela yukarıdaki **'_argümanlar'** konumunda harf dizisi matriksi var ve 
biz bunun derecesini 2 düşürdüğümüzde (**'\*\*_argümanlar'**); 
matriksteki [0,0] hücresindeki harfe erişiyoruz. 

Tıpkı nasıl geometride boyutlar var ise konumlarda içlerinde bulundurdukları veriye 
göre boyut anlamı kazanır ve işletim sistemi bu veriyi yapılandırılmış vereceği için dizilere erişir gibi erişilebilir.
Bu yönüyle yukadıraki örneği aşağıdaki gibi yazabiliriz:

.. code:: 

  iş Giriş2 
  argümanSayisi   tam,
  _argümanlar   **t8
  {
    //argümanları konumlarından yazdır.
    her i := 0; i < argümanSayisi; i++:
      stdio::printf(
        "=> konum değeri: %p, konumdaki değer: %s\n", 
         &_argümanlar[i], 
          _argümanlar[i]); 
  }

Bir önceki örnekle özünde aynı şeyi yapıyor ama fark ettiğiniz üzere 'argümanSayısı'
değeri bizim gezeceğimiz konumları sınırlıyor ve taşma tehlikesinin de önüne geçiyor.
Olmaz ama diyelim ki konumu arttırarak ilerlediğimiz 'Argüman' değeri boş konuma denk gelmedi.
O zaman işletim sisteminin yazılıma ayırdığı bölgenin dışına taşacağı için meşhur **'SIGSEGV'** 
hatasını verecek ve 139 kodu ile sonlandırılacak. 
Şunu da eklemek gerekir ki; gözlemlerimden çıkardığım sezgisel sonuca göre 
pek çok yazılımcı ilk dereceyi unutup boyut ve derece kavramını karıştırıyor. 
Kavramları karıştırarak tasarım yapmaya çalışmak da doğal olarak hatalı sonuçlar doğuruyor.
Bunlar göz önünde tutulunca ikinci yöntem daha güvenli. 
Ayrıca veri türü doğrusal olarak hem derleyici hem yazılımcı tarafından 
daha yapısal yorumlanıyor ve boyutlar derecelerin aksine elle tutup gözle görebileceğimiz bir kavrama 
dönüşmeye başlıyor. Doğal olarak tasarım bir kere cisimleşmeye başlayınca; olgunlaşıyor.

Konu konum kavramı iken eklenmesi gereken bir diğer mevzu bu örnekteki 'i' 
değerinin de bir konum olması. Dereceli değerlerle olan farkı dereceli değerler işletim sistiminin 
belirlediği standartlara uyarak hafızayı konumlandırıp erişirken; 
'i' değeri doğrusal yaklaşımla hafızaya erişiyor olması. 
Daha önce bahsettiğimiz sıralı numaralı boncuk dizisi örneğindeki konumlandırma yaklaşlaşımı ile 
buradaki 'i' değerinin yaklaşımı özlerinde aynı ve iki örnekte de doğrusal konumlandırma yapılıyor. 

**'Giriş2'** işlemindeki tek fark bu da değil. İkinci örnekteki print'in ikinci argümanı için yer alan
**(&_argümanlar[i])** ifadesinde konum alma işlemi kullanılırken, 
öncekinde üçüncü dereceden **(Argüman)** saf ifadesi yer almış ve ayrıca üçüncü argümandaki
**(\*Argüman)** ifadesi ise **'i'** kadar ilerlenmiş konumun tuttuğu değeri dönüyor. 
Sanki **'&'** (konumlandırma işlemi) ile **'\*'** (derecelendirme işlemi) birbirinin 
ters işlemi gibi hissediliyor ve yukarıdaki **tanımlı kavramların sınırında**; 
evet iki işlem birbirinin tersi oluyor. Konumlandırma işlemi var olan değerin konumunu getirirken; **'\*'**
işlemi var olan dereceli değerin tuttuğu konumun derecesini düşürüp; düşürülen değeri dönüyor. 

Ama bu ikisi de tekiller ve biz sıradaki konuma ulaşmak için tutulu konumu 
arttırmak ya da azaltmak zorundayız ki yukarıda anlattığımız gibi yan etkileri olan bir yöntem. 
Bu bağlamda dizi erişim işlemi gücünü gösteriyor. Dizi erişim işlemiyle, derecelendirme işlemi 
benzer görevleri paylaşsalarda aynı işlem değiller ama **konumdaki veriler ardışık** 
ise boyut kavramı hafızanın o **ardışık** parçasına diziymiş gibi erişmemizi sağlıyor. 
Mesela: 

.. code:: 

  iş BoyutKavramıÖrneği 
  {
    // işletim sisteminden ((t32'nin boyutu) X 20) bayt kadar 
    // hafıza bölgesi istiyoruz.
    Sayılar := yeni(t32[20]); 
    // işletim sisteminin bize temizlemeden 
    // verdiği bölgedeki t32'leri yazdırıyoruz: 
    her i := 0; i < 20; i++: 
      stdio::print("%d'ıncı pis değer : %d; konumu : %p\n", 
        i, Sayılar[i], &Sayılar[i]);
    // işimizi bitirdik ve bize atanan hafıza bölgesini 
    // işletim sistemine geri veriyoruz.
    sil Sayılar; 
  }

Derecelendirme işleminin soyutluğu; erişim işlemi ile kayboluyor ve 
biz zihnimizde işletim sisteminden gelen bölgenin aslında bildiğin t32'li boncuklar dizisi 
olduğunu canlandırmaya başlıyoruz ve bu noktada konumlar ve dizilerin birbirleri ile ilişkisi 
belirmeye başlıyor. 

.. note:: 
  Peki şu vaka ile karşılaşabilir miydik ? Biz işletim sisteminden yeni bölge istedik ama 
  gelen bölgedeki verilerin konumları ardışık değil. Linux ve Freebsd'de kesinlikle öyle değil ama diyelim ki 
  öyle biz nasıl dereceler kavramını kullanarak ileri, geri konum aritmetiği yapacaktık ? 
  Basitçe söyleyeyim yapamayacaktık. Eğer veri ardışık değilse zaten konum aritmetiği yapmanın 
  ne anlamı ve güvenilirliği var. Fakat boyutlar ile dereceler ve konumlar ile diziler arasındaki 
  kavram ilişkisi devam edecekti. Yine konumlara derecelendirerek erişecektik ve yine dizilere 
  boyutlandırarak erişecektik. Sadece dereceli erişim yavaş olacaktı ki konum erişimi destekleyen 
  canlı dillerde (C#, OCaml vs) konum erişimi yavaş olacaktı. 
  Çünkü işletim sistemi ile sizin yazılımınız arasında hafıza yönetimi yapan temizlik algoritması var
  ve her konuma eriştiğinizde zaten işletim sisteminin sanal olan konumlarını bir de temizlik algoritmasının 
  sanallaştırdığı konumları çözümlemeyi eklemek zorunda kalacaktık ve bu bize hız kaybettirecekti.

  O yüzdendir ki sistem dillerinin neredeyse tamamı hem temizlik algoritmalarını, 
  hem de sanal makinaları ve diğer aracı algoritmaları reddeder. Çünkü bu seviyede bir hız kaybı 
  işlevsel olarak kabul edilemez. Yazılımlarımızın öngörülebilir olmasını istiyoruz çünkü sistem dilleriyle
  genelde sürücüler, sanal makineler, işletim sistemleri, veritabanları vs gibi hayatî 
  yazılımların en kötü senaryolarındaki hızları üzerinden hayatî hız hesaplamaları yapıyoruz ve 
  her bir algoritmayı eklediğinizde, bu algoritmanın doğası nasıl olursa olsun, öngörülebilirlikten ödün 
  veriliyor. 

  Bu durumda şunu diyebilir miydik ? "Zaten işletim sistemleri ardışık verileri bize istediğimizde veriyor,
  hem sanal makinaların faydalarından yararlanır hem de sistem dillerinin hızlı doğasının tadını çıkarırdık."
  Bunu yapmak tabi ki de mümkün ve zaten pek çok dil yapıyor. Yukarıda andığım C# çok iyi tasarlanmış; 
  yıldırım hızında çalışan dillerden bir tanesi ama mesele o değil. Sistem dillerinin 
  tasarım amacı bilgisayarla aracısız konuşmak. Yani malı toptancıdan değil fabrikadan alıyormuşsunuz gibi 
  düşünün. 

  Daha önemlisi hız kazanmak için olguları ve sorunları olabildiğince doğrusal düşünmek gerekiyor. Yukarıdaki 
  t32X20'lik dizide ne yaparsan yap o diziyi gezmek için mecburen bir döngü kullanacaksınız ve 
  O(n) öngörüsünde çalışacaksınız. Yani 
  veri türünüz algoritmayı belirliyor. 2 boyutlu doğası olan bir tür için zorlasanız zorlasanız 
  O(nlog(n)) senaryosunda algoritma geliştirebilirsiniz ki bu şu anlama geliyor elinizdeki veriye göre 
  algoritma O(n^2) gibi de çalışabilir. Özet olarak kullandığınız tür algoritmanızı belirliyor. 

Derleyicide gerçekleşen şey ise çok basit, derecelendirme işlemi konum aritmetiği yapmadan 
dereceyi düşürüp tutulu konumdaki veriyi getiriyor; dizi gibi yorumladığı konumlar için ise  
konum aritmetiği yapıp derecesini düşürerek veriyi dönüyor. 

Çeviriler:
^^^^^^^^^^
Boyut ve derece kavramlarının kesiştiği yeri tartıştık ama bir soruyu cevaplamadık. 
Dizi erişim işlemi bir konumdan diğerine nasıl ilerliyor ya da geriliyor ? 
Basitçe cevap vereyim; genişliğine ve sıralama katsayısına göre. 

:: 
  Bu iki kavramı hafıza yönetimi 
  başlığı altında ayrıntılı bir şekilde tartışacağız ama  
  burada 'sıralama' kavramını hafıza yönetimindeki ilişkilerinden 
  bağımsızmış gibi düşünmemiz gerekiyor. 

İyi güzel de **'yeni'** işlemi özünde posix 
sistem çağrılarından biri olan **'malloc'** işlemine 
gönderme yapıyor ve o işlem bize **t8** dizisi dönüyor. Nasıl oluyor da 
**t8** dizisini bir türmüş ya da diziymiş gibi kullanıyoruz. ?
İşletim sisteminden alınan hafıza bölgesini, 
Örs derleyicisine hedef türün genişlik ve sıralama bilgilerine göre yorumlattırarak. 
Nesneler derlenirken, Örs onların genişlik ve sıralama bilgilerinin 
çok sıkı muhasebesini yapıyor. 
Yukarıda **'yeni(t32[20])'** işlemi çağrısının sade posix malloc çağrısından farkı 
bu muhasebeden kaynaklanıyor. 

Çeviri işlemi dönülen değere istenilen sıralama ve genişlik bilgilerinin muhasebesini ekliyor
ki taşma, yanlış okuma, boş konum vs gibi ciddi sorunlar 
derleme süresince yakalansın ve eğer muhasebe doğru 
yapılmıyorsa uyarı verilsin. 
Bu yönüyle çeviri işlemi gerçek işlem değildir. 
Derleyicinin genişlik ve sıralama muhasebesinin yönlendirilmesidir. 
'BoyutKavramıÖrneği' işlemini yeniden yazarak gösterelim: 

.. code:: 

  iş BoyutKavramıÖrneği2
  {
    Sayılar := <*t32>stdlib::malloc(20*@t32); 
    her i := 0; i < 20; i++: 
      stdio::print("%d'ıncı pis değer : %d; konumu : %p\n", 
        i, Sayılar[i], &Sayılar[i]);
    sil Sayılar; 
  }

Birinci örnekle özlerinde aynı ama çeviri işlemiyle 
**'Sayılar'** değerinin **t32** konumu olduğu belirtiliyor. Diğer taraftan **'yeni'** 
işlemi ise bu görevi gözlerden ırak bir şekilde zaten yapıyor ama gerçekleşen şey, sonuç, çıktı aynı. 


Konum çevrilerini sadece kaynak isterken değil, 
elimizdeki kaynaklar yorumlarken de kullanabiliriz. 
Mesela:

.. code:: 

  iş KonumYorumuÖrneği 
  {
    //onaltılık ascii değerleri içeren bir t64 sayısı başlatıyoruz.
    //ilk sekiz baytın 0 olduğunun altını çizerim.
    değer sayı t64 = 0x0_47_46_45_44_43_42_41;

    // t64 konumunu yeni değere atıyoruz.
    SayıKonumu := &sayı; 

    //t64 konumunu, t8 konumuna çeviriyoruz
    Harfler    := <*t8>SayıKonumu; 

    //Sonuçları yazdırıyoruz. 
    stdio::print("Sayı konumu: %p\nHarfler konumu: %p\nHarfler içeriği %s\n",
      SayıKonumu, Harfler, Harfler);
  }

Burada t64 sayı değerinin konumu harfler dizisiymiş gibi yorumlanıyor. 
Derleyici ise 8 bayt genişliğindeki ve 8 bayt sıralamasındaki t64 konumunu, 
1 bayt genişliğinde ve sıralamasındaki t8 değerleri tutan Harfler konumuna çeviriyor. 
Bu konunun altı belirgin bir şekilde çizilmeli, çevirme işleminin bilgisayar, işlemci, 
işletim sistemi için anlamı yok. Derleyiciler için var ki değerlerin konumlarını 
üretim sürecinde hesaplayabilsinler. 

Mesela:

.. code:: 

  iş ÇeviriÖrneği1
  {
    değer sayı t64 = 0x0_47_46_45_44_43_42_41;
    SayıKonumu := &sayı;
    Harfler    := <*t8>SayıKonumu; 
    Tamlar     := <*t32>SayıKonumu;
    Simgeler   := <*t16>SayıKonumu;
    stdio::printf(
      "Sayı Konumu: %p\nHarfler konumları:\n [0]:%p\n [1]:%p\n [2]:%p\n [3]:%p\n [4]:%p\n [5]:%p\n [6]:%p\n [7]:%p\n", 
      SayıKonumu, 
      &Harfler[0], &Harfler[1], 
      &Harfler[2], &Harfler[3], 
      &Harfler[4], &Harfler[5], 
      &Harfler[6], &Harfler[7]);
    
    stdio::printf(
      "Sayı konumu: %p\nSimgeler Konumları:\n[0]:%p\n[1]:%p\n[2]:%p\n[3]:%p\n",
      SayıKonumu, 
      &Simgeler[0], &Simgeler[1], 
      &Simgeler[2], &Simgeler[3]);
    
    stdio::printf(
      "Sayı konumu: %p\nTamlar Konumları:\n[0]:%p\n[1]:%p\n",
      SayıKonumu, 
      &Tamlar[0], &Tamlar[1]);
  }

  /*
    Benim bilgisayarımda böylesi bir çıktı veriyor: 
    Sayı Konumu: 0x7ffcc51683d0
    Harfler konumları:
    [0]:0x7ffcc51683d0
    [1]:0x7ffcc51683d1
    [2]:0x7ffcc51683d2
    [3]:0x7ffcc51683d3
    [4]:0x7ffcc51683d4
    [5]:0x7ffcc51683d5
    [6]:0x7ffcc51683d6
    [7]:0x7ffcc51683d7
    Sayı konumu: 0x7ffcc51683d0
    Simgeler Konumları:
    [0]:0x7ffcc51683d0
    [1]:0x7ffcc51683d2
    [2]:0x7ffcc51683d4
    [3]:0x7ffcc51683d6
    Sayı konumu: 0x7ffcc51683d0
    Tamlar Konumları:
    [0]:0x7ffcc51683d0
    [1]:0x7ffcc51683d4
  */

İşlemin çıktısından farkedeceğiniz üzere, 
**'Harfler'** dizisindeki konumlar teker teker,
**'Simgeler'** disisindeki konumlar çifter çifter, 
**'Tamlar'** dizisindeki konumlar ise dörder dörder artmış. 
Derleyici üretim aşamasında genişlik ve sıralama muhasebesini 
tutuyor ki, dizi erişim ve diğer konum işlemleri canlı çalışırken 
görevlerini verilerin ardışıklığını ve sıralamasını bozmadan icra edebilsinler. 


.. note:: 
  Bu örnekte bayt genişliği ve sıralamanın, dizi erişiminin ibresiyle birebir hareket 
  etmesi, kullanılan türlerin yapıtaşı olmasından kaynaklanıyor. Türler için 
  bayt genişliği ve sıralama illa ki aynı olacak diye bir kaide yok. 

-------------------

Şey:
^^^^

**'şey'** yapıtaşı; **'mimari'** genişliğinde olan ve içinde herhangi dereceden herhangi 
konumu tutan veya tutmayan yapıtaşıdır. 

Tıpkı nasıl ardışık türlerin ayağını yere bastırmak için dizi türünü tanımladıysak, 
konum kavramının da ayağını bir yapıtaşı ile yere değdirmemiz gerekiyor. 

C dilindeki dengi **'void*'** türüdür ama Örs dilinde 

Sonuç:
^^^^^^

Konumlar konusunda ne kadar çok kavram kümesiyle iletişimde bulunduğumuzu gördünüz. 
Yeni başlayanlar için göze korkutucu gelebiliyor ama ustalar için konumlara ayar çekebilme 
yeteneği büyük bir güç ve Örs bu konuda üzerinde iyi düşünülmüş araçlara sahip. 