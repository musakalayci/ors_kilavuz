**************
Temel İşlemler
**************

Yazılım dünyasında işlevi yönünden özüne indirgenmiş, görevi önceden tasarlanmış
ifadelere denir. 

Bu indirgemedeki hedef temel işlemin en az makina dili ile 
işlemci için ifade edilmesi, 
eğer indirgenemiyorsa mümkün olduğunca durağanlaştırılması; 
yani derleme sürecinde o işlemlerin sonuçlandırılmasıdır. Özüne 
indirgenmiş deyimiyle kastedilen budur. 

Bazı ifadeler ise yazılımlarda tekrar eder. Mesela çok fazla geçirme 
işlemi yapan algoritmalarda bu geçirme işlemi görevleri önceden 
tasarlandığı haliyle temel işlem olarak kullanılabilir. Görevi 
önceden tasarlanmış deyimiyle ise kastedilen budur. 

Canlı temel işlemler; işlemci tarafından çalıştırılabilirken;
durağan temel işlemler üretim sürecinde sonuçlandırılır. İlki işlemciyi 
hedef alırken; durağan temel işlemler derleyici hedef alır. 

Canlı temel işlemlerin 
makina dilinde birebir karşılığı bazen olabilir. Matematik, Mantık,
Konum, Erişim sınıfındaki işlemlerin genelde işlemci komutu karşılığı vardır. 
Diğer sınıfta canlı işlemler malesef aynı görevi üstlenmiş işlemci komutu almayabilir. 
Mesela **'+='** önce değer ile yapıtaşını toplayacak sonra ise sağdaki değere geçirecek. 
Bu temel işlemin işlemci komutlarında karşılığı olsaydı zaten yazılım dillerine gerek olmazdı. 

.. warning::
  Tekrar belirtelim; yapısal dillerdeki temel işlemlerin 
  hepimizin bildiği matematikteki temel işlemlerle alakası bile yoktur. 

  Hatta matematikten ödünç alınmış işlemlerin bile bize lise ve 
  üniversitede öğretilen işlemlerle alakası yoktur. Bize 
  sürekli matematik öğretilmiş iken 
  bilgisayar dünyasındaki matematik işlemleri sıralı 
  matematiğin alanına (ingilizcesi:discrete mathematics) girer.

Örs dili C ailesinin temel işlemlerini değiştirmemesine 
rağmen kendi içinde yeni temel işlemler de ekler. 

C++ dilinin aksine Örs temel işlemleri yeniden tanımlatmaya izin vermez. 
Nedeni ise yazılım dünyasında bu konuda bir anlaşmanın olmaması 
ve herkesin fevri simgelerle bir takım işlemleri kolaylaştırma 
çabasının kodu okunamaz hale getirmesidir.

C dil ailesinde tüm temel işlemler sola doğru döndüğü için Örs'de bu kaideye uyar.

Temel işlemler çeşitli özelliklerine göre sınıflandırılabilir. 
Aşağıda söz dizimine göre sınıflandırarak bu işlemleri tanıtacağız.

İkiz işlemler:
^^^^^^^^^^^^^^

**'(ifade) işlem (ifade)'** 
söz dizisiyle sağ ve sol ifadeler bekleyen işlemlerdir:

**Aritmetik:**

- **'+'**, **'-'** simgeleri sağ ve sollarındaki sayısal ifadeleri sırasıyla toplar ve çıkarır.
- **'*'**, **'\/'** simgeleri sağ ve sollarındaki sayısal ifadeleri sırasıyla çarpar ve böler. 
- **'%'** simgesi solundaki sayı türündeki değer sağındaki sayı türündeki değere bölününce kalan değerini verir.

**Bit:**

- **'&'** 
- **'|'**
- **'^'**
- **'~'**
- **'<<'**
- **'>>'**

**Mantıksal:**

- **'&&'**, **'ve'** simgeleri sağ ve sollarındaki sayısal değerleri mantıktaki 've' işlemi ile karşılaştırır.
- **'||'**, **'veya'** simgeleri sağ ve sollarındaki sayısal değerleri mantıktaki 'veya' işlemi ile karşılaştırır. 

**Karşılaştırma:**

- **'<'**: sayı türündeki değerleri niceliklerine göre karşılaştırır ve sağı küçükse 1 döner. 
- **'>'**: sayı türündeki değerleri niceliklerine göre karşılaştırır ve sağı büyükse 1 döner. 
- **'<='**: sayı türündeki değerleri niceliklerine göre karşılaştırır ve sağı küçükse 1 döner.
- **'>='**: sayı türündeki değerleri niceliklerine göre karşılaştırır ve sağı büyükse 1 döner.
- **'=='**: sayı türündeki değerler eşit ise 1 döner.
- **"!="**: sayı türündeki değerler eşit değil ise 1 döner.
  
**Atama:**

- **'+='**:  sağındaki değeri solundakiyle toplar ve soldaki değere geçirir.
- **'-='**:  sağındaki değeri solundakiyle çıkarır ve soldaki değere geçirir.
- **'*='**:  sağındaki değeri solundakiyle çarpar ve soldaki değere geçirir.
- **'\/='**: sağındaki değeri solundakiyle böler ve soldaki değere geçirir.
- **'%='**:  sağındaki değeri solundakiyle kalma işlemini uygular ve soldaki değere geçirir.
- **'<<='**: sağındaki değeri solundakiyle sola kaydırma işlemini uygular ve soldaki değere geçirir.
- **'>>='**: sağındaki değeri solundakiyle sağa kaydırma işlemini uygular ve soldaki değere geçirir.
- **'||='**: sağındaki değeri solundakiyle 'veya' işlemini uygular ve soldaki değere geçirir.
- **'&&='**: sağındaki değeri solundakiyle 've' işlemini uygular ve soldaki değere geçirir.
- **'~='**:  sağındaki değeri solundakiyle 'bit tersleme' işlemini uygular ve soldaki değere geçirir.
- **'&='**:  sağındaki değeri solundakiyle 'bit ve' işlemini uygular ve soldaki değere geçirir.
- **'|='**:  sağındaki değeri solundakiyle 'bit veya' işlemini uygular ve soldaki değere geçirir.
- **'^='**:  sağındaki değeri solundakiyle 'ters bit veya' işlemini uygular ve soldaki değere geçirir.

**Hafıza:**

- **'<-'**: Sağındaki konumun değerini dönüp; solundaki değere geçirir.
- **'<=>'**: Sağ ve soldaki konumların değerlerini değiştirir. 

**Arama:**

- **'::'**: Birimde tanımlı nesneleri arar ve bulursa döner. 
  Bulamazsa hata verip derlemeyi sonlandırır.

**Erişim:**

- **'->'**: Soldaki türün konumuna erişir ve sağındaki aranan ifadeyi tür üyesi olarak bulabilirse döner.
- **'.'**:  Soldaki türün değerine erişir ve sağındaki aranan ifadeyi tür üyesi olarak bulabilirse döner

Tekil İşlemler:
^^^^^^^^^^^^^^^

**Adım:** 

- **'(ifade)++'**: solundaki sayısal ya da konum ifadesinin değerini, 
  ifadeyi değerlendirdikten sonra, bir birim arttırır. 
- **'++(saf ifade)'**: sağındaki sayısal ya da konum saf ifadesinin değerini, ifadeyi 
  değerlendirmeden önce, bir birim arttırır. 
- **'(ifade)\-\-'**: solundaki sayısal ya da konum ifadesinin değerini, 
  ifadeyi değerlendirdikten sonra, bir birim azaltır. 
- **'\-\-(saf ifade)'**: sağındaki sayısal ya da konum saf ifadesinin değerini, ifadeyi 
  değerlendirmeden önce, bir birim azaltır.

**Konum:**

- **'\*(konum ifadesi)'**: Solunda verili konumun değerini döner. 
- **'&(değer ifadesi)'**:  Solunda verili değerin konumunu döner. 
- **'(konum ifadesi)[x]**: Solunda verili konumun x'inci sıradaki değerini döner.

**Tür nicelik:**

- **'@(ifade)'**: Solunda verili ifadenin bayt boyutunu döner.
- **'$(ifade)'**: Solundaki verili ifadenin bayt sıralamasını döner.

**Tür:**

- **'%(ifade)'**: Sağındaki ifadenin türünü döner. Üretim sürecinde anlamlı olsa da Örs durağan bir dil olduğu için;
  canlı anlamı yoktur.

Tanımlı yapıtaşları:
  .. list-table:: 
    :widths: 3 5 2 10 10 10 5 5
    :header-rows: 1

    * - **Temel İşlemler**
      - İsim
      - Tür
      - Makina Satırı Sayısı
      - Görev 
      - İşleme durumu
      - Okuma Yeri 
      - Eş Anlamlısı
    * - **Aritmetik**  
      -  
      -
      - 
      -  
      -  
      -  
      - 
    * - **+**  
      - artı
      - yapıtaşı
      - 1
      - aritmetik
      - canlı
      - orta
      - 
    * - **-**  
      - eksi
      - yapıtaşı
      - 1
      - aritmetik
      - canlı
      - orta
      - 
    * - \*  
      - çarpı
      - yapıtaşı
      - 1
      - aritmetik
      - canlı
      - orta
      - 
    * - **\/**  
      - bölme
      - yapıtaşı
      - 1
      - aritmetik 
      - canlı
      - orta 
      - 
    * - **%**  
      - kalma
      - yapıtaşı
      - 1
      - aritmetik 
      - canlı
      - orta 
      - 
    * - **Bit**  
      -  
      - 
      -  
      -
      -  
      -  
      - 
    * - **&**  
      - bit ve 
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **|**  
      - bit veya
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **^**  
      - bit ters veya
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **~**  
      - bit tersleme 
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **<<**  
      - sola kaydırma 
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **>>**  
      - sağa kaydırma 
      - yapıtaşı
      - 1
      - bit  
      - canlı 
      - orta 
      - 
    * - **Mantık**  
      -  
      - 
      -  
      -  
      -  
      -
      -
    * - **&&**  
      - ve 
      - yapıtaşı
      - satır > 1
      - mantık  
      - canlı 
      - orta 
      - ve
    * - **||**  
      - veya
      - yapıtaşı
      - satır > 1
      - mantık
      - canlı 
      - orta  
      - veya, ya_da 
    * - **!**  
      - değil 
      - yapıtaşı
      - 1
      - mantık 
      - canlı 
      - orta 
      -
    * - **Karşılaştırma**  
      -  
      - 
      -
      -  
      -  
      -  
      -
    * - **<**
      - küçüktür 
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **>**
      - büyüktür 
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **<=**
      - küçük eşittir  
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **>=**
      - büyük eşittir  
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **==**
      - eşitlik  
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **!=**
      - eşit değildir  
      - yapıtaşı
      - 1
      - karşılaştırma 
      - canlı 
      - orta 
      - 
    * - **Adım**  
      - 
      - 
      - 
      - 
      -  
      -  
      -
    * - **(..)++**  
      - arka artış 
      - yapıtaşı, konum
      - satır > 1
      - adım 
      - canlı 
      - son 
      -
    * - **++(..)**  
      - ön artış 
      - yapıtaşı, konum 
      - satır > 1
      - adım 
      - canlı 
      - ön 
      -
    * - **(..)\-\-**  
      - arka azalış 
      - yapıtaşı, konum 
      - satır > 1
      - adım 
      - canlı
      - son 
      -
    * - **\-\-(..)**  
      - ön azalış
      - yapıtaşı, konum 
      - satır > 1
      - adım
      - canlı
      - ön 
      -
    * - **Konum**  
      -  
      - 
      -  
      -  
      -  
      -
      -
    * - \*  
      - derecelendirme 
      - konum
      - 1
      - konum 
      - canlı 
      - ön 
      -
    * - **&**  
      - konumlandırma
      - konum 
      - 1
      - konum 
      - canlı 
      - ön 
      -
    * - **[]**
      - dizi erişim 
      - konum 
      - 1
      - dizi, konum 
      - canlı
      - son 
      -
    * - **Nicelik**  
      - 
      - 
      -
      -  
      -  
      -  
      -
    * - **@**  
      - boyut 
      - tüm türler 
      - 0
      - nicelik  
      - durağan  
      - ön 
      -
    * - **$**  
      - sıralama 
      - tüm türler  
      - 0
      - nicelik  
      - durağan 
      - ön 
      -
    * - **Atama**  
      -  
      - 
      -
      -  
      -  
      -  
      -
    * - **=**
      - eşittir  
      - tüm türler 
      - satır > 1
      - atama 
      - canlı 
      - orta 
      - 
    * - **+=**
      - artı eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **-=**
      - eksi eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **\*=**
      - çarp eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **\/=**
      - böl eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **%=**
      - kal eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **<<=**
      - sola kay eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **>>=**
      - sağa kay eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **||=**
      - veyala eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **&&=**
      - vele eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **~=**
      - bit tersle eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **&=**
      - bit vele eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **|=**
      - bit yadala eşittir  
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **^=**
      - bit ters yadala eşittir   
      - yapıtaşı
      - satır >= 2
      - atama 
      - canlı 
      - orta 
      - 
    * - **Tür Erişim**
      -    
      -
      - 
      -  
      -  
      -  
      - 
    * - **->**
      - tür alt konuma erişim   
      - türler
      - 2
      - tür erişim  
      - canlı 
      - orta 
      -
    * - **.**
      - türü indirgeme   
      - türler
      - 1
      - tür erişim   
      - canlı 
      - orta 
      -
    * - **Hafıza**
      -    
      - 
      -
      -  
      -  
      -  
      - 
    * - **<-**
      - geçirme   
      - ~
      - satır >= 2
      - hafıza  
      - canlı 
      - orta 
      -
    * - **<=>**
      - içerik değiştirme   
      - ~
      -   
      - hafıza 
      - canlı 
      - orta 
      -
    * - **Arama**
      - 
      - 
      -  
      -  
      -  
      -
      - 
    * - **\:\:**
      - arama 
      - birimler
      - 0
      - arama 
      - durağan 
      - orta 
      - 
    * - **Tür İfadesi**
      - 
      -
      - 
      -  
      -  
      -  
      - 
    * - **%**
      - tür alma 
      - tüm türler
      - 0
      - tür ifadesi
      - durağan 
      - ön 
      - 
    