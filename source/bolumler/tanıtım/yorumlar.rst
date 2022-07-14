Yorumlar
********

Örs dilinde yorumlar C ailesi söz dizimi kuralını uygular. 

.. glossary:: 
  Tek Satırlı: 
    .. code:: 

      //Toplama işlemi için tek satır yorum örneği.
      iş Topla a tam, b tam: tam => 
        dön a + b; //tek satırlı yorum.  


    Tek satırlı yorumlar için '\/\/' simgesi ile başlanıp yeni *metin satırında* biter. 
    Burada altını çizmek isterim metin satırları yani '\/n' ile simgelendirdiğimiz ascii 
    kodu '0x0A' olan kavram ile Örs derleyicisinin satırlardan anladığı şey bambaşka şeylerdir ve 
    kesinlikle karıştırılmamalıdır. Bu konuya satırlar konusunda değineceğiz. 

  Çok Satırlı:  
    .. code:: 

      /*
        Toplama işlemi için 
        çok satırlı yorum örneği. 
      */
      iş Topla a tam, b tam: tam => 
        dön a + b; //tek satırlı yorum. 

    Çok satırlı yorumlar için '\/\*' simgesi ile başlanıp '\*\/' bitirilir.

  Kılavuz: 
    Yorumlar kavram olarak yazılımcıların çalışırken ilk önce 
    kendi kendilerine tuttukları notlar olarak değerlendirilebilir. O yüzden derleyici '.ors' belgesindeki yorumları anlamlandırmaz ve çözümleme aşamasında geçilir. 

    Tabi ki de faydaları tartışılamaz ama kılavuz üretiminde kullanışlı değillerdir. 
    Alakalı önemi ise Örs doğasında açık kaynak destekleyen bir dil ve kılavuzu yazılmamış 
    açık kaynak yazılımların piyasada bir önemi olmamaktadır. Bu yönüyle Örs dilinin kılavuz 
    yetenekleri en az yazılımdaki yetenekleri kadar önemlidir. Çünkü diğer mühendislerin 
    okuyup anlayamadığı ve dolayısıyla kullanamadığı kodun açık kaynak dünyasında pek yaşama 
    şansı yoktur. 

    .. code:: 

      {*
        kılavuz::örnek_kütüphane::Topla += 
          tanıtım: "Tam sayılar için toplama işlemi yapar",
          değişkenler: {...},
          örnek: "x := 22;\\n 
                  y := 33;\\n
                  z := Topla(x, y)";
      *}
      iş Topla a tam, b tam: tam => 
        dön a + b;

    Yukarıdaki örnekte olduğu gibi kılavuz açmak için '{\*' simgesi ile başlanır; 
    kılavuz öğesi yazılır ve '\*}' simgesi ile kapatılır. 

    Kılavuz hazırlama konusunu daha ayrıntılı bir şekilde kılavuz bölümünde ele alacağız. 

  Kaideler: 

    **Yorumlar derleyici tarafından satırmış gibi algılanır.**
    O yüzden ifadeler arasında yorum bulunamaz. Yani aşağıdaki örnek 
    Örs derleyicisi tarafından reddedilecektir. 
      
    .. code:: 
      
      değer i tam = a * //bir takım şeyler 
        b; 
      
    **Kılavuz yorumları sadece \'birim\'lerde yer alabilir.**
    Zira işlem bedenlerinde kılavuzun anlamı yoktur. Bu bağlamda kılavuz yorumları 
    birim'lere dahil edilir. 



