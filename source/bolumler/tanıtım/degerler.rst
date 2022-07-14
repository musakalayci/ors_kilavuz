Değerler
********

Özlerinde amacı bir takım veriler üretmek olan yazılımların başlangıç ve sonuçlarını 
saklamak için değer kavramına ihtiyacımız var. 
Bu konuda çeşitli tartışmalar ve aşırıya kaçan çözümler olsa da Örs, 
C dillerinden yani bilgisayarın kalbine doğrudan erişimi olan 
dillerden olduğu için, tanımlı tüm değerlerin bilgisayar belleğinde fiziki konumu vardır ve 
bu konum sanal yollardan erişilebilir.

Örs'de söz dizimi farkıyla iki türlü değer tanımı yapılabilir. Açık ve Pascal tanımı. 

.. glossary::

  Açık tanım: 

    .. code::

      değer sayı        tam;.
      değer _birşeyler  metin; 
      değer _utf_metni *t8; 

      değer yaşım tam     = 29; 
      değer _mahmut metin = "Ikinci Mahmut"; 

    
    Burada söz diziminden anlaşılacağı üzere "değer" kelimesi ile değer tanımlandığı
    tetiklenir, sonrasında değerin benzersiz ismi gelir, sonrasında ise değerin türü. 
    Değer tanımlamak için bu kadarı yeterlidir ama bu şekliyle değerlerin ilk değerleri 
    belirlenmemiştir. Dolayısıyla bu değerlerin hafızada tuttuğu veriye ulaşıldığında 
    elimize ne geçeceğini bilemeyiz. O yüzden isteğe bağlı olarak, yukarıda olduğu gibi, değerler "=" simgesi 
    ile başlatılabilir. 

  Pascal tanımı: 

     .. code::

        gelen   := belge::aç(); 
        yaşım   := 29; 
        _mahmut := "İkinci Mahmut";

     Pascal tanımlarda ise değerin ilk değerinin olduğu varsayılır. 
     Bu yönüyle tanımın türü en baştan bellidir ve diğer söz dizileri gereksiz kalır. 
     Tasarım amacı okunmayı kolaylaştırmaktır. 
     Görsel kullanışlılığı dışında tüm fiziki, yani bilgisayarın gördüğü, 
     özellikleri "değer" kavramı ile aynıdır. İsmini ise Pascal yazılım dilinden alır. 
     Çeşitli yazılım dillerinde Pascal tanım satırını görebilirsiniz. 
