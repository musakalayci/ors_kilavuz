***
Boş
***

Sayılar için 0 değerini; türler için sıfırlanmış üyeleri;
konumlar için ise yokluğu tanımlayan
saf ifadelerdir. Yani saf halleriyle daha anlamlıdırlar.
Anlamları üretim sürecinde yorumlanır. 

C dilindeki 'void' değillerdir ve bu yönüyle '\*boş' gibi bir ifade 
hata verir zira olmayan konumun değerini nasıl alacaksınız. 

.. code:: 

  değer i tam = {};
  değer j tam = 0;
  değer k tam = boş;

Örnekteki tanımlı değerlerin hepsinin içeriği 0'dır. 

.. code:: 

  tür ikili
  {
    a tam;
    b tam;
  }

  iş Örnek 
  {
    değer a_ve_b ikili = {};
    değer b_ve_a ikili = boş;
    //sıradaki ise hata verir;
    değer hatalı ikili = 0;
  }

Örnek işleminin ilk iki satırında 'ikili' türündeki değer yaratılır ama 
içeriği sıfırlanmıştır. Üçüncü satırda ise hata alacağız çünkü ikili türünün 
içeriğinde sayı yapıtaşları olsa da kendisi sayısal yapıtaşı değildir.
