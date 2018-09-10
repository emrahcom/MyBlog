Gerçek zamanlı bir Linux masalı
===============================

### Cahil Cesareti
Bir gün [Linus](https://en.wikipedia.org/wiki/Linus_Torvalds) adında bir genç,
yaşına başına bakmadan bir işletim sistemi çekirdeği (kernel) yazmaya başlamış.
Cahil cesareti diye buna deniyor herhalde. Başlamış kodlamaya... Yazdıkça
yazmış, yazdıkça yazmış. O sırada bir kahkaha sesi duyulmuş. Linus umursamamış,
yazmaya devam etmiş. Üç bin, beş bin satır derken kodlar çoğalmaya, çalışan bir
şeyler ortaya çıkmaya başlamış. Bu sefer '*mikro kodla*' diye bir ses duyulmuş.
Sağa sola bakınmış, kimseyi görememiş. Yazmaya devam etmiş. Sonunda çalışan bir
çekirdek çıkmış ortaya. Bunu arkadaşlarına göstermiş, arkadaşları çok beğenmiş.
Hatta bazıları makinesine kurup kullanmaya başlamış. O bilmiş ses bi daha
duyulmuş: '*mikro kodla*'

Linus sağa sola bakınmış kimse yok. Başını kaldırıp kürsüye bakınca orada
oturmakta olan [Tanenbaum
Hoca](https://en.wikipedia.org/wiki/Andrew_S._Tanenbaum)'yı görmüş.

> **Tanenbaum Hoca**   
> *Evladım, kaç yılındayız biz?*   
>
> **Linus**   
> *1992*   
>
> **Tanenbaum Hoca**   
> *1992 yılında
> [Monolithic_kernel](https://en.wikipedia.org/wiki/Monolithic_kernel)
> yazılır mı? Ne bulduysan koymuşsun çekirdeğin içine... Kim yapacak bu kodun
> bakımını? Ya bi hata yaparsan, bütün sistem çöker valla*   
>
> **Linus**   
> *Hocam iyi ama...*   
>
> **Tanenbaum Hoca**   
> *[Mikro çekirdek](https://en.wikipedia.org/wiki/Microkernel) yazacaksın.
> Çekirdek dediğin ayak işlerine bakmaz. Dosya sistemini, hafızayı filan bırak
> da hizmetçiler halletsin. Yoksa senin çekirdek, başkalarının hizmetçisi
> olur.*   
>
> **Linus**   
> *Hocam, güzel diyorsun da bak
> [Richard Stallman Abi](https://en.wikipedia.org/wiki/Richard_Stallman) mikro
> çekirdek yazacam diye yıllarını harcadı, saç sakal birbirine karıştı ama
> hala ortada bir şey yok. [Emacs](http://www.gnu.org/software/emacs/) bile
> bitti, çekirdek bitmedi.*
>
> **Tanenbaum Hoca**   
> *Bak hala konuşuyor. Dua et benim öğrencim değilsin, yoksa sınıfta kalmıştın.*

Linus, '*bu akademisyen tayfası adam olmaz*' diye içinden geçirip, bildiği gibi
yoluna devam etmiş. Sonunda ortaya oldukça yetenekli ve hızlı bir çekirdek
çıkmış. GNU araçları ile de bu çekirdeği birleştirince GNU/Linux işletim
sistemi doğmuş. Bu işletim sistemi çok tutmuş, her yerde kullanılmaya
başlanmış.


### Mühim Adamlar
GNU/Linux'un başarısı, [hard
real-time](/2009/04/gercek-zamanli-sistem-nedir.md#soft-real-time-ve-hard-real-time)
sistemler tasarlayan mühim adamların kulağına gitmiş. '*Şu GNU/Linux'u
bir de biz görelim, belki işimize yarar*' demişler. Toplanıp Linus'u ziyarete
gitmişler.

> **Mühim adamlar**   
> *Slm*   
>
> **Linus**   
> *Slm*   
>
> **Mühim adamlar**   
> *Senin çekirdeği, bizim işlerde kullanmak istiyoruz. Sence olur mu?*   
>
> **Linus**   
> *Ben çekirdeğime güveniyorum. Her işin üstesinden gelebilir*   
>
> **Mühim adamlar**   
> *Hmm, tamam öyleyse bir deneme yapalım. Şimdi ben şu topu havaya atacam,
> senin çekirdek yere düşmeden vuracak, tamam mi?*

Mühim adam topu havaya atmış, '*pat*'... Çekirdek anında havada vurmuş topu.

> **Mühim adamlar**   
> *Hmm, güzel... Bir deneme daha yapalım.*

Bir top daha atmış, '*pat*' vurmuş. İki, üç derken sıra onüçüncü topa gelmiş.
Mühim adam topu havaya atmış, çekirdekte hiç bi hareket yok. Herkes şaşkın
birbirine bakınmış. Linus çekmiş çekirdeği kenara.

> **Linus**   
> *Hayrola?*   
>
> **Çekirdek**   
> *İşim vardı, topa bakamadım*   
>
> **Linus**   
> *Nasıl bakamadın?*   
>
> **Çekirdek**   
> *Abi, önemli işim vardı. Kesip topa bakamadım*   
>
> **Linus**   
> *Dalga mı geçiyorsun sen benle? Bunlar mühim adamlar. Ne işin varsa kesip
> bunlarınkine bakacaksın*   
>
> **Çekirdek**   
> *[Kritik
> bölgedeyken](https://en.wikipedia.org/wiki/Critical_section#Kernel_Level_Critical_Sections)
> nasıl keseyim işi*   
>
> **Linus**   
> *Keseceksin,
> [pre-emptive](/2009/04/gercek-zamanli-sistem-nedir.md#pre-emptive-nedir)
> olacaksın*   
>
> **Çekirdek**   
> *Sen bilirsin abi*

Linus, mühim adamlara dönüp '*tamam hallettim sorunu, bi daha olmayacak böyle
bir şey*' demiş. Yeniden başlamışlar top atmaya. Çekirdek pek bi pre-emptive
hareket etmiş başlarda. Baya bi top vurmuş ama doksan dokuzuncu topta yine
kaçırmış.

> **Mühim adamlar**   
> *Hmm, bu olmamış, bizim işleri beceremez*

deyip gitmişler. Linus ve çekirdek kalmış başbaşa.

> **Linus**   
> *Niye kesmedin yaptığın işi*   
>
> **Pre-emptive çekirdek**   
> *Bu sefer gerçekten çok önemli işim vardı, gerçekten kesilecek gibi
> değildi*   
>
> **Linus**   
> *Ben sana gösteririm önemli işi. Seni
> [Ingo Molnar](https://en.wikipedia.org/wiki/Ingo_Molnar)'a göndereyim de,
> herbir yerini un ufak etsin. Kesilemeyecek işin kalmasın*   
>
> **Pre-emptive çekirdek**   
> *Ama Tanenbaum Hoca demişti sana. Yıktın bütün işleri bana, hangisine
> bakacağımı...*   
>
> **Linus**   
> *Sus!*


### Bu işi çözse çözse Kerim Yağmur çözer
Bu arada mühim adamlar da sonuçtan memnun değilmiş. Kendi aralarında durumu
değerlendirmeye başlamışlar.

> **Mühim adam 1**   
> *Yok, bu çekirdek bizim işi görmez*   
>
> **Mühim adam 2**   
> *Evet görmez*   
>
> **Mühim adam 1**   
> *Halbuki üzerinde ne de güzel yazılımlar çalışıyordu. İşimizi görseydi,
> hepsi elimizin altında olacaktı*   
>
> **Mühim adam 3**   
> *Öyle ama monolitik yazmış çekirdeği. Bi sürü kritik bölge vardır kodda*   
>
> **Mühim adam 4**   
> *Evet. Kritik bölgeye girdi mi, çıkana kadar top çoktan yere düşer.*   
>
> **Mühim adam 1**   
> *Kritik bölgedeyken işi yarım bırakıp bizimkine bakamaz mı?*   
>
> **Mühim adam 3**   
> *Teoride olur ama bütün kritik bölge kodlarını baştan yazmak lazım.
> Çoook uzun iş ve yine de güven olmaz*   
>
> **Mühim adam 1**   
> *Öyleyse bu iş yatar, eski sistem devam ediyoruz*   
>
> **Mühim adam 4**...
> *Bi de Kerim Yağmur'a sorsak. O teknik konularda iyidir, belki aklına bir
> şey gelir*   
>
> **Mühim adam 3**   
> *Hmm soralım*

Toplanıp hep birlikte [Kerim Yağmur](http://www.opersys.com/)'a gitmişler.

> **Mühim adamlar**   
> *Slm Kerim, bizim bir sorun vardı*   
>
> **Kerim Yağmur**   
> *Evet?*   
>
> **Mühim adamlar**   
> *Güzel bir işletim sistemi var, GNU/Linux Bizim işlerde kullanmayı düşündük
> ama çekirdek monolitik. Milyonlarca satır kod var içinde. İşleri
> toparlayıncaya kadar top yere düşüyor.*   
>
> **Kerim Yağmur**   
> *Hmm, öyleyse QNX kullanın*   
>
> **Mühim adamlar**   
> *QNX kullanıyoruz zaten ama GNU/Linux üstünde çok güzel yazılımlar var,
> onları istiyoruz*   
>
> **Kerim Yağmur**   
> *Siz şimdi GNU/Linux üstünde çalışan servis ve yazılımları mı istiyorsunuz
> yoksa yeni bir gerçek zamanlı işletim sistemi mi?*   
>
> **Mühim adamlar**   
> *Asıl istediğimiz servis ve yazılımlar*   
>
> **Kerim Yağmur**   
> *Öyleyse iş kolay. Yazarız bir gerçek zamanlı mikro çekirdek, GNU/Linux'u
> onun üzerinde servis olarak çalıştırırız*   
>
> **Mühim adamlar**   
> *O zaman GNU/Linux bizim işleri yapabilecek mi*   
>
> **Kerim Yağmur**   
> *Sizin işleri, yazacağımız gerçek zamanlı mikro çekirdek halledecek ama
> GNU/Linux'da bir yanda çalıştığı için onu da kullanabileceksiniz*   
>
> **Mühim adamlar**   
> *Linus bozulmasın kendi işletim sisteminin servis olarak çalışmasına*   
>
> **Kerim Yağmur**   
> *Yok yahu, niye bozulsun*   
>
> **Mühim adamlar**   
> *Adam bi garip. Zaten '**mikro**' kelimesini duyunca gözü seğirmeye başlıyor,
> sinirli oluyor*   
>
> **Kerim Yağmur**   
> *Tamam canım, biz de mikro değil,
> [nano çekirdek](https://en.wikipedia.org/wiki/Nanokernel#Nanokernel) deriz.
> Adını da [ADEOS](https://en.wikipedia.org/wiki/Adaptive_Domain_Environment_for_Operating_Systems)
> koyarız.*

O sırada bir kahkaha sesi duyulmuş.
