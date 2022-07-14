Yapıtaşları
===========

Örs dilinde hafızada konumlandırabileceğiz en küçük anlamlı parçalardır. 

Konumlandırabileceğiz diyoruz zira türleri üyelerine ayrıştırınca 
öyle bir noktaya erişiyoruz ki daha fazla parçalamak yazılımda 
verim, hız, bütünlük gibi sorunlara yol açıyor. 

Bu noktada yazılım dilleri tüm tanımlanabilir türlerin 
temel alacağı yapıtaşları belirler. 

Bunu yaparlarken genelde güttükleri kaygı uyumluluk üzerinedir. 
Mesela işlem çağrılarını birbirine giren parçalar olarak hayal edin. 
Eğer parçalar belli bir ölçüye uymuyorlarsa beraber çalışmaları zorlaşır ve hatta imkansızlaşır. 
Bu noktada işlemciler tarafından belirlenen mimarilere uymak 
ve tür temelinde genel uyumu yakalamak önemlidir. Bu mânada; 
hayalen dilediğiniz bit genişliğine sahip yapıtaşlarını hem makina dili 
hem de yazılım dili seviyesinde tanımlamak tamamen mümkündür.
Sistem dilleri için sorun bu bit genişliğinin işlemci mimarisi ile uyumlu olup olmadığıdır. 
Zira hedefi makina kaynaklarına sağlıklı erişim olan dillerin; mimari uyumsuzluğu yüzünden 
hız ve verim sorunlarına katlanmasını beklemek biraz anlamsızdır. 

Yukarıdaki uyum sorunu cidden önemli çünkü aynı zamanda yazılımımızı dış dünyaya
bu yapıtaşlarının ele alanışı üzerinden belirliyoruz. Eğer derleyici tarafından
belirlenen genişlikler yaygın kullanıma uymuyorsa, iki iletişim kaynağının 
arasına görevi çevirmenlik yapmak olan bir yazılımı eklemek zorunda kalıyoruz. 

Bu yüzden Örs yapıtaşları konusunda C'dili ile bire bir uyumluluk siyasetini güder. 
C dilinde bile derleyiciden derleyiciye değişen ve hatta sürümler arası farklar olan 
bir konuyu daha da karmaşıklaştırmak anlamsız ve gereksizdir. 

En nihayetinde gerçek hayatta yazılımdaki görevleri bir araya getirerek türler oluşturmaktır ki
kendileri de aynı zamanda türdür. Türlerden farkı en küçük anlamlı konumladırılabilir parçalar olmasıdır. 
Onun dışında türlerle aynı davranışları sergilerler. 

Aşağıda Örs dilinde tanımlı yapıtaşlarına ve C'deki denklerine ulaşabilirsiniz.


Tanımlı yapıtaşları:
  .. list-table:: 
    :widths: 5 5 25 25 10 5 5
    :header-rows: 1
      
    * - **Yapıtaşları**
      - Bit genişliği
      - Alt sınır 
      - Ust sınır 
      - İşaretli mi 
      - C'deki karşılığı
      - Biçimlendirme 
    * - **Tam Sayılar**  
      - 
      - 
      - 
      - 
      -  
      -  
    * - **t8** 
      - 8 bit
      - -127
      - 128
      - evet 
      - char
      - %c 
    * - **t16** 
      - 16 bit 
      - -32,768
      - 32,767
      - evet 
      - short
      - %hd 
    * - **t32** 
      - 32 bit 
      - -2,147,483,648
      - 2,147,483,647
      - evet 
      - int 
      - %d
    * - **t64** 
      - 64 bit 
      - -2^63
      - 2^63
      - evet 
      - int64_t
      - %lld 
    * - **t128** 
      - 128 bit 
      - -2^127
      - 2^127
      - evet 
      - __int128_t
      - %lld* 
    * - **tam**  
      - 32 bit 
      - -2,147,483,648
      - 2,147,483,647
      - evet 
      - int 
      - %d
    * - **Doğallar**  
      - 
      - 
      - 
      - 
      - 
      - 
    * - **d8** 
      - 8 bit
      - 0
      - 255
      - hayır 
      - uint8_t 
      - %c
    * - **d16** 
      - 16 bit 
      - 0
      - 65,535
      - hayır  
      - uint16_t
      - %hu
    * - **d32** 
      - 16 bit 
      - 0
      - 4,294,967,295
      - hayır
      - uint32_t
      - %u  
    * - **d64** 
      - 64 bit 
      - 0
      - 2^64
      - hayır
      - uint64_t
      - %llu  
    * - **d128** 
      - 128 bit 
      - 0
      - 2^128
      - hayır
      - __uint128_t 
      -   
    * - **doğal**  
      - 32 bit 
      - 0
      - 4,294,967,295
      - evet 
      - uint32_t
      - %u  
    * - **Ondalıklar**   
      - 
      - 
      - 
      - 
      - 
      - 
    * - **o32** 
      - 32 bit
      - ~
      - ~
      - ~ 
      - float
      - %f
    * - **o64** 
      - 64 bit 
      - ~
      - ~
      - ~ 
      - double
      - %lf
    * - **o128** 
      - 128 bit 
      - ~
      - ~
      - ~
      - ~  
      - %Lf
    * - **ondalık** 
      - 64 bit 
      - ~
      - ~
      - ~ 
      - double 
      - %lf
    * - **Özel**  
      - 
      - 
      - 
      - 
      - 
      - 
    * - mimari 
      - işlemci
      - ~
      - ~
      - hayır  
      - size_t
      - %lu  
    * - şey  
      - işlemci
      - ~
      - ~
      - ~
      - void*  
      - %p


        