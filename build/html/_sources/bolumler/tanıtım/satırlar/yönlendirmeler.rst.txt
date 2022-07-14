**************
Yönlendirmeler
**************


İşlem yönlendirmeleri:
----------------------

'git' satırı: 
^^^^^^^^^^^^^

İşlemciyi isimlendirilmiş kesite yönlendirir.
Genellikle döngüleri yönetilirken kullanılır. 
Her ne kadar namı kötü duyulsa da 
özellikle anlamlandırılacak metin ağaçlarını 
doğrusal alanda işlerken sıklıkla kullanılır. 

'git' satırı arkasına işlem konumu bekler. 


.. code:: 

  iş OnKereYaz
  {
    i := 0; 
    #kesit1 
    stdio::printf("ilk kesit\n"); 
    #kesit2 
    stdio::printf("ikinci kesit\n"); 
    eğer i < 10: 
    {
      eğer i % 2: 
        git kesit1; 
      değilse: 
        git kesit2;
    }
    
  }

Bu örnekte sadece nasıl kullanılacağı gösterilmiştir ve 
'git' satırının uygun kullanımına örnek değildir. 
Zira yukarıda 'her' döngüsü gerekmektedir. Konu ile alakalı
sağlıklı örnekler metin işleme algoritmalarından verilebilir ama 
zaten o algoritmalar dolama gibi olduğundan amacın dışına çıkılacağı düşünülmüştür.

'dön' satırı:
^^^^^^^^^^^^^

İşlem tanımlandığında belirlenen çıktı olgunlaşınca bu satır ile dönülür. 
Boş çıktısı olan işlemler için ifade kabul etmezken, aksi durumlarda ifade ister ve 
istenilen ifadenin konumu işletim yığınına konulur.

.. code::  

  iş ÇiftMi a tam: tam => 
    eğer a % 2:
      dön hayır; 
    değilse: 
      dön evet;

Yukarıdaki örnekte görüldüğü gibi dönülecek ifadelerin türü ile iş çıktısı aynı olmalıdır. 
Aksi takdirde derleyici hata verecektir.

Döngü yönlendirmeleri:
----------------------

'devam' satırı:
^^^^^^^^^^^^^^^
İstenilen durumlarda döngüyü sonraki devire atlatır. 
Tekildir.

'son' satırı: 
^^^^^^^^^^^^^
İstenilen durumlarda döngüyü sonlandırır. Yukarıda tanımlanan 'git' satırına 
muhalefeten tasarlanmıştır. 

.. code:: 

  iş ÇiftseYazdır:
    her a := 0; evet; a++:
    {  
      eğer !(a % 2): 
        stdio::printf("Çift sayı"); 
      eğerki a >= 10: 
        son; 
      değilse: 
        devam; 
      stdio::printf("a sayısı tekil olduğunda buraya ulaşılamayacak.");
    }

Gayet okunabilir olan yukarıdaki sonsuz döngüde a çift sayı ise değeri 
yazdırılacak, a değeri 9'u aştığında ise 'son' yönergesiyle sonladırılacak,
diğer koşulda ise döngüye diğer kesitlere uğranmadan devam edilecek.

Durum yönlendirmeleri:
----------------------

'tekrar' satırı:
^^^^^^^^^^^^^^^^
İçinde bulunduğu durum satırını
her bir 'tekrar' satırına uğranış için çalıştırır. 

'geç' satırı: 
^^^^^^^^^^^^^
İçinde bulunduğu seçim satırının ardılı olan seçim satırına 
atlamak için kullanılır. 

.. code:: 

  iş HarfseYaz _girdi *t8
  {
    i := 0; 
    durum _girdi[i];
    {
      seçim ascii::Boş: 
        dön;
      seçim 
        ascii::küçükler, 
        ascii::büyükler,
        ascii::Alt_Tire:
          stdio::printf("%c", _girdi[i]); 
          geç;
        varsayılan: 
          i++;
          tekrar;
    }
  }


Yukarıdaki örnekte _girdi ascii harfi dizisindeki okunabilir 
olanlar yazılacak, 
ve sonraki varsayılan satırında sırası arttırılıp durum 'ascii::Boş' sabitini görene kadar 
tekrar değerlendirilecek.


