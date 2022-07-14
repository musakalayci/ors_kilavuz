********
Metinler
********

Harf
^^^^
Hepimizin bildiği 8 bit genişliğinde ascii simgeleridir.
Unicode ve daha geniş verileri kabul etmezler. 
Varsayılan türleri harf yani 't8' türüdür.

Tıpkı diğer C ailesi üyeleri gibi 'a' şeklinde ifade edilirler. Mesela:

.. code:: 
  
  değer a harf = 'a';
  b           := 'b';
  c           := 0x63_st8;


Harfler
^^^^^^^
Boyutu durağan belirlenmiş harf dizileridir. 
Utf8 ve Unicode kabul ederler. 
Sıralandıklarında tek bir dizi gibi kabul edilirler.

.. code:: 

  değer ö *t8 = "örs dili";
  sıralı := "Sıralandıklarında"
    "tek bir dizi gibi"
    "kabul edilirler";

Örs'de harfler türü mimari türünün bayt boyutunun katlarıdır ve sıralıdır.
