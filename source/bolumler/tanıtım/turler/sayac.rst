Sayaç
=====

Örs dilinde konumlandırılamayan türlerdendir. 

Konumları alınamaz çünkü aslında kaynak kodunu anlamlı 
kılmak adına kümelendirilmiş sabit 32 bit genişliğinde tam 
sayılar **kümesidir.**

Tüm yazılım dillerinde farklı söz dizimleriyle bulunan bir kavramdır. 

.. code:: 

  sayaç Rakam
  {
    Sıfır = 0; 
    Bir; 
    İki; 
    Üç;
    Dört = 4; 
    Beş;
    Altı; 
    Yedi; 
    Sekiz; 
    Dokuz; 
  }


Yukarıdaki örnekte C dilindeki 'enum' kavramından farklı değil. 
Atamalardan sonra diğer üyeler birer arttırılarak değerlenecek. 
C dilinden farkı sayaçların üye olarak sayaç üyelerini kabul eden kümeleri de kabul etmesidir.
Çünkü sayaçlar yazılımda 'durum' kavramının tamamlayıcılarıdır ve 
bazen farklı durumlar için aynı seçim satırını kullanabiliriz. 
Tam bu noktada birden çok seçim satırını tekrar tekrar yazmak sadece 
kalabalık oluşturuyor ve okumayı güçleştiriyor. Bu noktada 
yardıma sayaç kümeleri yetişiyor. Mesela yukarıdaki örneği tekrar yazalım: 

.. code:: 

  sayaç Rakam
  {
    Sıfır = 0; 
    Bir; 
    İki; 
    Üç;
    Dört = 4; 
    Beş;
    Altı; 
    Yedi; 
    Sekiz; 
    Dokuz; 
    
    tekler(Bir, Üç, Beş, Yedi, Dokuz); 
    çiftler(Sıfır, İki, Dört, Altı, Sekiz);
  }

Burada tek ve çift sayılar tekrar kümelenmiş ki kullanımlarında kolaylık olsun. 
Mesela: 

.. code::

  iş RakamTekMiÇiftMi a tam
  {
    durum a 
    {
      seçim Rakam::tekler: 
        stdio::printf("Tek rakam: %d\n", a);
      seçim Rakam::çiftler: 
        stdio::printf("Çift rakam: %d\n", a);
      varsayılan: 
        stdio::printf("Gelen sayı %d bir rakam değil !\n", a);      
    }
  }

Yukarıdaki örnekte okuma kolaylığını görebiliyorsunuz. Sayaç kümeleri burada 
kodu daha sade ve okunabilir kılmış ki gerçek hayatta bu durumu bolca kullanıyoruz.
