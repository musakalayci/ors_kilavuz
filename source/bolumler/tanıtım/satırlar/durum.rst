*****************
Durum ve Seçimler
*****************

Dijital tasarımın özü. Hadi şu "dijital" kelimesinden kurtulalım. 
Zira herkesin aklına fotoğraf makinesi geliyor. 
Sayısal tasarımın özü: Durumlar. 

---------

Durum satırlarının amacı sabit sayı ile ilişkilendirilmiş satırları çalıştırmaktır. 
**Düz mantıkla** şunu söyleyebiliriz ki derleyici kod kesitlerini diziye koyuyor ve 
işlemci ise erişilen dizideki kodu çalıştırıyor olarak **kabaca** anlaşılabilir.  
Özlerinde sıralı kod kesitleri oldukları 
için matematikteki, işlevsel dillerdeki benzer kavramlarla örtüşmezler. 

Durum satırı baş kısmında tam sayı, özel olarak 't32', yapıtaşını bekler ve eğer satırdaki ifade 
't32' değilse üretim aşamasında 't32' türüne çevrilir. Özetle eğer siz durumunu seçmek için türü d64 olan 
bir ifade kullandığınızda bu siz çeviri yapsanız da yapmasanız da derleyici tarafından 't32' türüymüşcesine algılanır ve 
çeviri yapmadığınız taktirde kendisi çevirir. 
Bu kısım özellikle 'sayaç' kavramı ile bağlantılıdır. Hatırlarsanaz sayaçlar da 
üye olarak sadece 't32' sabitleri bekler.

Beden kısmında ise **seçim** satırları yer alır. 
Seçim satırına dahil olmayan satırlar varolduğu taktirde derleyici tarafından 
gereksiz görülecek ve silinecektir. 
Seçimler sabit sayılar, sabit sayı dizileri ve sayaç kümeleri beklerler. 
Değişken bir ifadenin seçim satırı olamaz. Eğer seçim satır başlarında verili ifadeler sabit değilse; derleyici hata verir ve üretimi durdurur. 
En nihayetinde üretilecek olan kod kesitini değişen sıraya koymanın ne imkanı ne de anlamı vardır. 

Seçimler beden olarak seçim satırı hariç her herhangi bir satırı kabul ederler. 
Bu uygulamada şu anlama gelir: 
İki seçim sıralandığı takdirde sonraki gelen öncekinin devam kesiti değildir. 
Aşağıda örnekle tekrar belirteceğiz. 

'**varsayılan**' satırı özel isimlendirilmiş bir seçim satırıdır. 
Seçmediğiniz tüm durumlar için varsayılan satırında seçilir. Adı üzerinde bizim ele almadığımız durumlarda 
yazılımın varsayılan davranışını belirler. Eğer durum satırlarınızda 'varsayılan' seçimi belirtmediğiğniz taktirde 
derleyici sizin varsayılan seçim için boş satır (yani: '{}' simgesi ile belirtilen satır) 
seçtiğinizi algılar.  
    
.. code:: 
        
  iş DurumÖrneği 
  {
    değer gelen tam = Sıfırİle10ArasındaRastgeleSayı();

    durum gelen: 
    {
      seçim 0: 
        stdio::printf("0 geldi.\n");
      seçim 2: 
        stdio::printf("2 geldi ve sıradaki seçime geçildi.\n");
        geç;
      seçim 1: 
        stdio::printf("1 geldi.\n"); 
      seçim 3, 4, 5, 6: 
        stdio::printf("3 <= durum <= 6 geldi.\n");
      varsayılan: 
        stdio::printf("Seçilmeyen bir durum geldi.");
    }

    //durumSatırıSonu 
    stdio::printf("örnek tamamlandı.\n");
  }

Yukarıdaki örnekte gelen sayısına sıfır ve 10 dahil ama arasında bir değeri atandı. 
Bu dakidan sonra yapılacak olan şey sizin belirlediğiniz seçim satırlarını çalıştırmak. 
Seçim satırları yönlendirilmediği taktirde durum satırı sonuna geçecekler ve görevlerini tamamlayacaklar. 

Altını çizerim bu C'deki \'switch/case\' satırlarından oldukça farlı ki zaten isim değişikliğinin nedeni bu farklılık. 
Eğer özel olarak belirtilmezse C dilindeki seçim satırları sıradaki satıra geçiyor. Cidden çok sıkıntılı ve tehlikeli bir özellik. 
Bazı durumlarda gözden kaçan, veya koymayı unuttuğunuz tek bir yönergenin neden olduğu hataları ayıklamak saatler alabiliyor. Dahası 
Dahası bazı durumlarda hatayı aylarca fark etmiyorsunuz ve ummadığınız bir zamanda başınıza bela olabiliyor. 

İkinci seçimde ise çok özel **\'geç\'** satırımız var. 
Gelen sayı 2 olduğunda 'seçim 2' satırı çalıştırılacak ama durum sonuna atlamak yerine 
'seçim 1' satırına geçecek ve tabi ki 'seçim 1' satırı işi bitince durum sonuna atlayacak. 

Durum döngüsü:
==============

Özellikle metin işleme ya da oyun yazılımlarında çok karşılaşacağınız bir sorun. 
Belirlediğiniz duruma kadar döngü devam etsin istiyorsunuz. 
Sanal makinalarda genellikle sıfır durumuna kadar döngü bitsin istemiyorsunuz. Mesela: 

.. code:: 

  iş BelgeYaz _yol *t8 
  {
    Belge := belge::bayt::Yeni(_yol); 
    eğer Belge:
    {
      sıra := 0; 
      durum Belge.Dizi[sıra]: 
      {
        seçim 0: 
        varsayılan: 
          stdio::printf("%c", 
            Belge.Dizi[sıra++]); 
          tekrar; //can alıcı kısmı. 
      }
    }
    değilse:
      stdio::printf("%s belgesinin içeriği okunamadı.\n");
  }

Burada yapılan iş basitçe ilkin belge bayt olarak açıldıktan sonra 
bayt dizisine erişiliyor. Belge sonlarında sıfır olduğu için 'seçim 0' durum sonuna atlayıp devam edecek. 
Diğer tüm seçimler için ise, sıradaki harfi yazdırıp sonra durumu tekrar edecek. 
'tekrar' sözcüğünün örs için anlamı bu. 

Doğal olarak sadece seçim satırlarında yer alabilir ve kümelenmiş durum satırlarında 
'tekrar' satırı kullanıldığında en son durum satırına atıfta bulunur ve oraya atlar. 
Bunun dışındaki yerlerde tekrar yönerge satırı anlamsızdır ve hatalıdır. 
Derleyici uygun kod ile işlemi hatalı sonlandıracaktır. 

Şu denilebilir ki "Bu çok tehlikeli bir özellik, ne gereği vardı, döngü kullanılarak da başarılabilirdi" vs. 
Hepsine \"Evet haklısınız\" diyorum ama yukarıda 
belirttiğim gibi bu biraz elinizdeki soruna yönelik bir çözüm. 
Belirttiğim gibi tekrar satırı metin çözümleme 
ve oyun tasarımı gibi alanlarda anlamlı ve üretken çözümler sunar. 

Döngülerde özellikle her döngüsünde baş satırlar anlamlı olduğu için 
işlem gücüne mâl olur. Metin sorunları ise doğaları gereği hız isteyenler olduğundan 
her bir küçük işlemden bile olabildiğince kurtulup hızın sıkıp suyunu çıkarmamız gereken durumlarda 
Durum döngüleri anlamlı olur. 

Tekrar belirtmek isterim gündelik durumlarda beklenmeyen, tehlikeli sonuçlara yol açabilir. 
En nihayetinde eğer döngü varsa bunu yönergelerle değil döngü satırları ile sağlamak 
hem okunabilirlik, hem sadelik ilkelerinin taleplerini sağlamak bakımından önemlidir. 

Durum ve seçim satırları görevleri gereği C dilindeki 'switch/state', işlevsel dillerdeki 
'the guards' kavramlarına benzer. Yukarıdaki farklılığı belirtmek adına kavramları doğrudan 
çeviri yöntemiyle isimlendirmek uygun görülmedi. Diğer dillerde ve Örs dilinde 
ifadenin durumuna göre seçim yapıldığı için konuşma dilindeki sözcüklerden ilham alındı. 


  
   