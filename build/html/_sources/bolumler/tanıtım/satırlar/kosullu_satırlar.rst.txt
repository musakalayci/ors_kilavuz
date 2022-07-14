****************
Koşullu Satırlar 
****************


Yazılımdaki yönlendirmeleri mantık kullanarak yapabileceğimiz, 
sıralı bağlanabilen satırlardır. 

-------

Koşullu satırların amacı, 
yönlendirme satırlarını mümkünse işlev dışı bırakıp, 
bu satırları derleyiciye makina dili ile örtülü şekilde ürettirmek, 
kodun okunabilirliğini arttırmak, hata ayıklamayı kolaylaştırmaktır. 

Koşullu satırlar baş kısımlarında 'eh' türlü ya da 'eh' türüne çevrilebilen  
ifade bekler. Eğer ifade 'eh' yapıtaşına çevrilemiyorsa derleyici hata verir. 
Sayısal değerler eğer 0 dan farklı ise eksi ya da arto olmasının bir önemi olmaksızın 
tıpkı diğer sistem dilllerinde olduğu gibi \"evet\" yani 1 kabul edilirler; tam tersi durumda ise \"hayır\" 
yani 0 kabul edilir ve çevrilirler. 

Konumlar da özlerinde sayısal değer olduklarından; 
eğer ki verili konum 0 değilse \"evet\" kabul edilir 
ve konum boş olduğunda ise \"hayır\" kabul edilirler. 

Beden kısımlarında ise herhangi bir satırı kabul ederler. 

'eğer' satırı yukarıdaki özelliklere uyar, tekil olarak kullanılabilirler
ama diğer koşullu satırlardan 
farklı olarak arkasında koşul sağlanmadığında yönlendirebilecekleri 
'eğerki' ya da 'değilse' satırlarını bekleyebilirler. 

'eğerki' satırı yukarıdaki özelliklere uyar ama tekil olarak kullanılamazlar. 
'eğerki' satırının aldığı koşul sağlanmadığında yönlendirebileceği 
'eğerki' veya 'değilse' satırlarını beklerler. 
'eğerki' satırı bedeni tekil satır değilse ve 
sonrasında 'eğer' satırı gelmişse derleyici hata verir ve süreç durdurulur. 

'değilse' satırı yukarıdakilerin aksine değerlendirecekleri koşul beklemezler. 
Koşulların önceki 'eğer' veya 'eğerki' satırlarında değerlendirildiklerini 
varsayarlar. 'değilse' satırı bu doğası gereği tekil olamaz. 

.. code::  

  iş ÇiftMi a tam; tam: 
    eğer a % 2:
      dön hayır; 
    değilse: 
      dön evet;

Yukarıdaki örnekte basitçe görüleceği gibi, 
eğer 'a' değerinin modu bir ise bedenindeki koda yönlenecek 
değilse; sıradaki 'değilse' satırına yönlecek. 

Bu örnekte görüldüğü gibi davranışları C ve benzeri dillerdeki 
'if/else \.\.' satırları ile bire bir örtüşür. 

