********
Birimler 
********

Örs dilinde çözümlenen söz dizisinin ilk ürünü olarak kabaca tanımlanabilir. 

.. warning:: 

  Örs'teki birim özelliğini lütfen, sakın ki sakın 
  nesne tabanlı dillerdeki özelliklerle karıştırmayınız. 

Kabaca diyorum çünkü bu konu göründüğünden daha derin. 
C'de her bir '.c' belgesi genelde '.o' belgesine çevrilir. 

.. note::
  
  Yazının devamında;

  | '.o' uzantılı belgeye **nesne** belgesi,
  | '.a' uzantılı belgeye **dahili** kütüphane, 
  | '.so' uzantılı belgeye ise **harici** kütüphane

  diye atıfta bulunacağız.


Nesne belgelerinin içeriğinde basitçe makina koduna yorumlanmış 
işlemleriniz ve yazılımınızın hafıza iskeleti bulunur. 
Durağan değerlerin hafızada nasıl canlanacağı bilgisi bu belgededir.
İşlemler ise yalındır. Yani dahili ve harici kütüphanelerle
nasıl iletişime geçeceği bilgisini bulundurmaz. 

Eğer diğer kütüphanelerle sade yöntem olan işlem çağrıları ile 
iletişim kursaydık ve bu işlem çağrılarının küresel değişken 
değerler kullanmadığını varsaysaydık bu konu tüm dillerde 
basmakalıp ele alınırdı ama ne güzel ki gerçek öyle değil. 

Nesne belgeleri yazdırılıp üretim süreci tamamlanınca isteğe göre bağlama süreci başlar. 
İsteğe bağlı diyorum çünkü ürünler illa ki bağlanmak zorunda değil. Çünkü bağlama 
sürecinin yazılım dilleri ile alakası bile tartışılabilir. Yaygın kullanım isimleriyle
'.a' ve '.so' uzantılı belgelerinin biri dahili bağlanmışken diğerinde sadece harici atıflara 
nasıl canlı ya da yazılım hafızaya alınırken bağlanacağı bilgisi vardır. 
Sistem dilleri genelde bu sorunun işletim sistemine ait olduğu varsayımı ile hareket ederler ki 
pek çok zaman sistem dillerini derletmek içim 'cmake' gibi yazılımları 
kullanmamızın ana nedenlerinden biridir. Bir takım kütüphanelere atıfta bulunacağız ama
bu belgelerin nerede olduğunu bilmiyoruz sorununa çözüm üretirler. 

Diğer taraftan örs dili türlerinin neden değişken türlü 
işlemler tanımlamamasının kökünde yatan nedenlerden birisi de budur. 
Örste değişken türlü sanal işlemler tanımlayabiliyorken; değişken türlü işlemler 
tanımlanamıyor. Şimdi bunun her bir tür başlatılıp işlem çağrıldığında yeniden işlemin 
derlenmesi sorunu bir tarafa aynı zamanda bağlama sürecinde de sıkıntı yaşatıyor. 
Burada bu özelliğe sahip diller iyi ya da kötü dillerdir diye bir argüman savunmuyoruz. 
Bu bambaşka bir tartışma konusu. Birimlerle alakası bu işlemlerin nasıl bağlanacağı ve 
konumlarının nasıl belirleneceğidir. Örnek vermem gerikirse; 
diyelim ki C++ mantığında derleme yapan bir dil ile;
bir yerde 'dizi<tam>' türünde, 
başka bir yerde ise 'dizi<hesaplar>' diye iki farklı tür tanımladınız. 
Eğer kalıp taçları konum olsaydı neyin konumu olmaksızın tür aynı olacaktı ama değil. 
Peki yorumlanan türleri aynı olmayan dizi kalıbının işlemleri ne olacaktı ? 
Tüm bu işlemleri ya her çağrıldıklarında yeniden derleyecektiniz ya da değeri birinci dereceden 
konummuş gibi hayal edip yığın çizelgesi oluşturacaktınız. 
Üçüncü çözümde ise hiç derlemeyip sanal işlemmiş gibi ele alacaktınız ama o kavram zaten 
Örs için tanımlı ve geriye elinizde 2 çözüm kalıyor. 
Peki bu işlem atfı yığın çizelgesini nasıl bağlattıracaktınız ? 
C++ dilinin namının şaibeli olmasının temel nedenlerinden bir tanesi bu çok ciddi sorun bu arada. 
Bu ciddi soruna 'Sanal İşlemler' konusunda tekrar değineceğiz. 
Birimlerin nasıl ele alındığı 
ve nasıl algılanması gerektiği ile derinden alakalı temel bir sorun olduğu için 
hatırlatma ihtiyacı duyduk. 


Birim kavramının amaçlarından bir diğeri ise 
isim çakışmasını ve dolaşmasını engellemektir. 
Mesela elinizde ekleme yapan birden fazla birim olduğunu düşünün. 
Farzedelim ki bunlardan biri 'dizi' diğeri 'çizelge' birimi olsun. 
Bu iki birimde doğal algoritmalarının bir parçası olarak 'ekle' işlemi tanımlayacaktı. 
Eğer Örs bu iki birimi tek birim olarak ele alsaydı; 
bu işlemlerin isimleri çakıştığı için hata vermek zorunda kalacaktı. 
Birim kavramı işlevde bu dolaşmanın da önüne geçer. 

Altı çizilmesi gereken bir diğer konu Örs'teki 
birimler kavramı kesinlikle nesne tabanlı dillerle karşılaştırılmamalıdır. 
Örste birimden kasıt 'CU' yani üretim süreci kavramı olan 'compilation unit' 
diye ingilizce tabir edilen kavrama ve bu kavramın üretilmiş haline, 
yani '.o' belgeleri ve alâkalı türevlerine atıfta bulunur. 
Bizim istediğimiz şey basitçe; bu ürünlerin nasıl bir araya getirilip kütüphanelere 
dönüşeceğinin belirgin olmasıdır. Bu mânada birim kavramının amacı derlemenin
tarama, çözümleme, üretim ve bağlama süreçlerinin olabildiğince örtüşmesi ve 
bu yazılımlar hayata geçtiğinde birbirleri ile iletişim kurarken tasarlanma sürecindeki 
kavram kümesi ile ortak kavram alanında kesişmesidir. 
Zira sistem dilleri için yukarıda 
özetle anlatıldığı gibi nesne belgelerinin üretiminden sonra yazılımınız özünde bir 
soyutlama olan yazılım dilinden epey ayrışıp;
gerçek hayattaki görev ve ilişkileri ile örtüşmeye başlamaktadır. 
Kavramların olabildiğince örtüşük olmasını 
istiyoruz ki on binlerce kütüphanenin birbirine dolanırcasına bağlandığı ve 
tüm bu süreci denetlemek için ayrı yazılımların kullanıldığı cengâmelere saplanma olasılığımızı 
düşürebilelim. 

Çünkü hoşumuza gitse de gitmese de üretilen 
birimler birbirleri ile ilişkilerine göre dallanıp, 
derecelenmeye ve ağaçlanmaya başlıyor. 

Daha ilginç olanı ise kaynağınızda dosya yaratmışsınız ve bu dosya genelde yukarıda 
bahsettiğimiz ilişki ağacının bir parçası oluyor ama pek çok yazılım dili bu dosyaları 
birim olarak kabul etmiyor. 

Birimler tüm bu yukarıdaki bahsettiğimiz dallanma sorununu, derecelenmeyi,  
yazılım dili seviyesinde çözmeye yarayan, içeriğinde derlenebilir öğeleri küme olarak tutan 
ve izdüşümü nesne belgeleri olan kavramlardandır. Bazı dillerden farkı 
sizin kaynak kodu ağacınızla örtüşük olmasıdır. 

.. warning:: 

  Tekrar uyarmak gerekiyor. Aşağıdaki örnek basitliği için seçilmiştir. Lütfen 
  birim özelliğininin nesne tabanlı tarzla ne bire bir örtüştüğünü ne de 
  öyle bir gayesi olduğunu biliniz. 

.. code::  

  dahili merkez::c::stdio;

  birim işlemler  
  {
    birim katlı
    {
      iş Çarp a tam, b tam: tam => 
        dön a * b;
    }
    iş Topla a tam, b tam: tam => dön a + b;
    iş Topla a tam, b tam: tam => dön a - b;
  }

  iş SonuçYaz: tam 
  {
    stdio::printf(
      "işlemler::Topla       = %d\n"
      "işlemler::katlı::Çarp = %d\n, 
      işlemler::Topla(11, 22), 
      işlemler::katlı::Çarp(11, 22));
  }


Yapılan şey şu örnekte diğer dillerden farklı değil. 
İşlemi tanımladık ve giriş işleminden çağırdık. 
Fark edeceğiniz üzere tanımlı birimlerden işlem çağırabilmek için birimin içeriklerine erişmek 
gerikiyor ve bunu '\:\:' simgesini kullanarak yapabiliyoruz. 

'SonuçYaz' işlemi fark ettiğiniz üzere anlamlandırdığınız ağaçta en üst seviyede. 
Bu bağlamda elimizde üretilmesi gereken 3 farklı birim var. Bağlama sürecinde 
çalıştırma belgesi, dahili veya harici kütüphene üretilecek olduğunda 
yapılacak olan şey basitçe 'işlemler::katlı' birimi işlemlere eklenecek ve bağlanacak; 
'işlemler' birimi de üst birime eklenecek ve toplanacak. 

Bir diğer örnek varsayılım ki elimizde aşağıdaki gibi
her bir işlemin ayrı belgede ele alındığı; gayet yaygın olan bir kaynak ağacı var: 

::

  birim_örneği 
  ├── işlem          
  |   ├── katlı
  |   |   └── çarpma.ors 
  |   ├── çıkarma.ors 
  |   └── toplama.ors
  └── sonuç_yaz.ors 

Bu dosya ağacının oluşturacağı birim ağacı ile bir üst örnekte 
oluşacak olan birim ağaçları bire bir aynı. 
Tek fark kaynak kodunuzu düzenleme tercihiniz ki o size kalmış. 
Ama Örs derleyicisi eğer dosya açıp içine kaynak kodu koymuşsanız bunu birim olarak kabul eder 
ve yukarıdaki bağlama sürecine tabi tutar. 

Tam burada birimlerin nasıl ele alındığı iyice belirginleşmeye başladı. 

**Peki ya Örs dili dahili veya harici kütüphaneleri nasıl görüyor ve ele alıyor ?** 

Yukarıdaki kaynak ağacını tekrar ele alalım. 

::

  birim_örneği 
  ├── özelleştirme.uzn  
  ├── işlem          
  |   ├── katlı
  |   |   └── çarpma.ors 
  |   ├── çıkarma.ors 
  |   └── toplama.ors
  └── sonuç_yaz.ors 

Sadece aşağıdaki uzengi satırını dosya kökündeki; 
'özelleştirme.uzn' belgesine yazmak yeterli olacaktır. 

.. code:: 

  özelleştirme:
    ad: "birim_örneği",
    çıktı: birim_örneği,
    ürün_türü: çalıştırma;
 
:: 

  Hatırlatma: 
  Ürün türünü belirlemek için; 
  'nesne'      : yalın nesne belgesi, 
  'çalıştırma' : çalıştırılabilir tetik belgesini, 
  'makina'     : makina dili,
  'dahili'     : dahili kütüphane, 
  'harici'     : harici kütüphane 
  seçenekleri; ilgili çıktıları üretir. 

