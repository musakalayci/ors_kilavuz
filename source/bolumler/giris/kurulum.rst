Kurulum
=======



Gerekli yazlımlar:

Freebsd için 
------------

.. code:: console

    $ pkg install llvm[10+] clang[10+] python[3+] cmake[3+] git 

Tercihen valgrind kurabilirsiniz.

.. code:: console 

    $ pkg install valgrind
    
Eğer freebsd'de clang atfı yoksa: 

.. code:: console 

    $ ln -s /usr/local/bin/clang[10+] /usr/local/bin/clang 

Eğer python atfı yoksa: 

.. code:: console 

    $ ln -s /usr/local/bin/python[3+] /usr/local/bin/python  


Linux için
----------- 

Pacman yazılımı kullanan Arch Linux türevleri için: 

.. code:: console 

    $ pacman -Syu llvm clang python[3+] cmake git 

Ubuntu ve Debian türevleri için: 

.. code:: console 

    $ apt install llvm clang python[3+] cmake git 


Gerekli yazılımlar yüklendikten sonra 

.. code:: console 

    $ git clone  https://github.com/musakalayci/ors.git 
    $ cd ors 
    $ ./baslat.py -d 


.. warning::

    Eğer ki eğer 'baslat.py' belgesi çalıştırılamıyorsa 

    .. code:: console 

        $ chmod -x ./baslat.py 

    komutu ile belgeyi çalıştırılabilir hale getirmelisiniz. 


Yukarıdaki komutlar ile örs derleyicisini C derleyicisine derlettirip kurabilirsiniz. 
LLVM arayüzünün çalıştığı her ortamda Örs kullanılabilir hale gelecektir. 
Şuan itibari ile Örs kaynak kodu C dilinden oluşuyor ama Örs beta aşamasına geçtiğinde 
kendi kendisini derleyecek yetiye sahip olacaktır ve ilk sürümde 
hem derleyicinin dili hem de ortamının örtüşmesi sağlanacaktır.


