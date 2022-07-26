Satırlar:
*********

Yazılım dünyasında meşur bir tartışma konusu var. 
Gerçekten kılavuzun tamamında bu tartışmaya atıflar var ve değinmemiz gerektiğini düşünüyorum. 

Kod kalitesini ya da miktarını **0x0A** ascii numarası ile anlamlandırılan yeni satır 
imgesi ile ölçebilir miyiz ölçemez miyiz ?

Böyle bir şeyin neden tartışılması gerektiği bir yana; gülünç bir 
şekilde alakalı isteği iş başvurusunda gördüm. 
İşveren ilanında "en az on bin satır kod yazmış olan." diye şart koşmuş. 

Burada kastedilen şey ne olabilir ki ? Eğer kastedilen şey 
\"üretiğiniz yazılımlarınızda ne kadar **'0x0A'** 
kodu var ?\" ise zaten öyle saçma yazılım şirketinde çalışılmaz, o işverenle iş yapılmaz. 
Mesela jquery.min.js kütüphanesi tek metin satırlı. Örs ve benzeri dillerde hiç satırla 
yazılım üretmeniz fevkâlade mümkün ve anlamlı. 

Diğer taraftan kastedilen **şey** eğer ki eğer bizim yazılım okurken algıladığımız **şey** ise 
gerçekten anlamlı ve derin doğaya sahip bir **şey** ile karşı karşıyayız ve bu **şey**\'in ne 
olduğu hem Örs derleyicisi için hem de bu kılavuz için çok önemli. 

Basitçe örnek vermem gerekirse: Ayak deyince aklınıza gelen ilk **şey** kendi ayağınız mı, 
masanızın ayağı mı, yoksa sandalyenin ayağı mı ? Tamam, dediniz ki \"Kendi ayağım\". 
Kaç tane ayağınız var ? İki. Peki ayak tanımını 
\"Sizin ayakta durmanızı sağlayan uzuv.\" olarak tanımlayıp 
tekrar \"Kaç ayağınız var ?\" diye sorsam ? 
Elleriniz üzerinde, kafanız üzerinde de ayakta durmanız mümkün. Elleriyle ayakta durarak 
yürüyen engelli insanlar, kafalarının üzerinde ayakta durup raks eden dansçılar var. 

\"Ya ne alakası var yazılımla bunun yine delirdi Musa !\", değil mi ? 
Deliliğe daha geliyoruz biraz sabredin. 
Size daha "işlemci kaç satır görüyor peki ?" diye sorup dumur edeceğim. 

Diyelim ki ayak deyince aklınıza masanızın ayağı geldi. Yine yukarıdaki diyalektiği 
takip edelim. "Masanızın kaç ayağı var ?" diye sorsam ve ben yukarıdaki ayak tanımına uyarak cevap versem. 
Mesela benim masam kutu tasarımına sahip ve bacak gibi kesilmiş kerestelerle değil 
levhalarla ayakta duruyor ve 3 farklı levha parçası var ama tasarım kutu tasarımı olduğu için 
kutunun yan yüzü olarak görürsem 1 parça var. 

Tekrar ayak uzvumuza geri dönelim. "Sizin ayakta durmanızı sağlayan uzva ayak denir." tanımı ile 
topuklarımın üzerinde ayakta durduğum için topuklarımı da ayak sayabilir miyim ? 
Peki balerinler parmakları üzerinde ayakta duruyor o zaman 
Evet ve bunu ısrarla uzatıp iletişim kuramını kullanarak matematikle de kanıtlarım. 

Şimdi bizim satır deyince yazılımda algıladığımız **şey** ne ? 
Bizim gördüğümüz mü ? Yani **0X0A** kodu mu ? Yoksa algıladığımız mı ? 
Yoksa Örs derleyicisinin gördüğü mü ?
Yoksa derleyicinin algıladığı mı ? İşlemcinin çalıştırdığı mı ? 
Bizim Kasabın et doğradığı mı ? Yoksa hepsi mi ? 

Artık internek kanallarından, gazetelere kod satırları haber olunca; yazılım dünyasında kullanılan 
satır kelimesinin hangi **şey**\'e atıfta bulunduğunu belirlememiz ve terim haline getirmemiz gerekiyor. 

Önerdiğim tanım: 
"Yazılım dilleri dünyasında satırlar sıralı ifadelerin anlamlandırılmış kümesidir." 

Örs ve diğer yazılım dilleri de satırları **sıralı ifadelerin kümesi** olarak algılar. Örnek verelim:

.. code:: 
   
   her değer i tam = 0; i < 10; i++: 
      her değer j tam = 0; j < 10; j++: 
         a := i + j;


Şimdi yapılan satır tanımıyla birlikte yine yukarıdaki diyalektiği yapmaya çalışalım. 
Yukarıdaki kod kesitinde kaç satır var ?

Gördüğümüz 3 satır var ama algıladığımız satırları saymaya başlayalım. 

Her döngüsü var, sonra bedeni var, 
o bedende bir döngü daha var ve onun da bedeni var yani dört diyebilir miyiz ? 
Tutarlı olur mu ? En nihayetinde tutarlı olması lazım ki hem derleyici anlayabilsin 
hem de bilgisayar çalıştırabilsin. 

Peki derleyici kaç satır görüyor ? Bu örnek için (3 + 1) + (3 + 1)  satır. 
Peki ya işlemci kaç satır çalıştıracak ? Yukarıdaki örnek için (3 + 1) X (3 + 1). 
Yani nam-ı diğer hepimizin bildiği O(n^2).
Özünde veri ağaçları olan satırların elamanları derleyici tarafından artarak algılanıyor 
diğer taraftan işlemci ise katlayarak algılıyor. Bu konuda yanlışım varsa düzeltilmek isterim. 
Zira ya benim liseyi tekrar okumam gerekiyor ya da biri birisinin alt türevi. 

Şimdi malum soruya geldik. İşlemci kaç satır görüyor ? 

Yukarıdaki tanıma göre görmüyor bile. İşlemcinin baktığı yerden hepsi aslında mimari biti 
genişliğinde dizi. 
Tıpkı Turingin tanımladığı gibi. 
İşletim sistemi yazdığınızı doğrusal olarak hafızaya geçirecek ve 
işlemciyi sizin kodunuzu koyduğu konuma yönlendirecek. 
Hatta yukarıdaki örnek, Örs, C, C++ vb dillerin iyileştiricileri 
tarafından da satır olarak görülmeyecek. Çünkü yukarıdaki döngünün hiçbir görevi yok. 
O yüzden işlemcinin calıştıracağı satır derken aslında örtülü bir varsayımda bulunup, derleyicinin iyileştirme 
seçeneklerinin kapalı oldunu düşünürek söylüyoruz. 

Tam da buralarda satır tanımlamasının rengi bozulmaya başlıyor. 
Kendine verilen alanın dışına çıkıyor. 
İşte tam bu noktada satır tanımı görevini tamamlamış oluyor. Bu kılavuzda satır kelimesini duyunca aklınıza sadece yukarıdaki tanım gelsin. 
Bir matematikçinin, işlemci tasarımcısının, hatta ve hatta güvenlik ve iyileştirme kaygısı güden 
yazılımcının kaç satır algılayacağını bilmenin pek bir imkanı yok. Mesela önceki paragrafta iyileştirme aşaması için 
yukarıdaki örneğe döngü dedim. 
Kümelenmiş iki döngü demedim; \"... döngünün hiçbir ... \" dedim. 
Çünkü iyileştirmenin özünde yan etkileri en aza indirmek var ve 
gereksiz koddan ziyade yan etki olabilir mi ? 
Mâna bu olunca burada tek satırlık bir döngü var orada ama iyileştirici algoritması iç döngünün içerisindeki etkisiz atamayı tespit edene kadar satır sayacak. 

Bakınız konu o kadar derinleşmeye başladı ki altında ezilmeye başladım. Fark ettiyseniz mâna kelimesini kullandım. 
Anlam kelimesini kullansaydım aklınıza \"Bizim anladığımız mı? Derleyicinin anladığı mı ?\" diye sorular gelecekti.
Örsün tasarım amaçlarından en güzeli belki de işte bu. Nihayet rüyâ görürken, sinirlenince konuştuğumuz dille bu harika konuları tartışabileceğiz. 
