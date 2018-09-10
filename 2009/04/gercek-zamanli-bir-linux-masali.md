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

<big><pre>
**Tanenbaum Hoca**
     *Evladım, kaç yılındayız biz?*
**Linus**
     *1992*
**Tanenbaum Hoca**
   *1992 yılında [Monolithic_kernel](https://en.wikipedia.org/wiki/Monolithic_kernel) yazılır mı?
   Ne bulduysan koymuşsun çekirdeğin içine... Kim yapacak bu kodun bakımını?
   Ya bi hata yaparsan, bütün sistem çöker valla*
**Linus**
   *Hocam iyi ama...*
**Tanenbaum Hoca**
   *[Mikro çekirdek](https://en.wikipedia.org/wiki/Microkernel) yazacaksın.
   Çekirdek dediğin ayak işlerine bakmaz. Dosya sistemini, hafızayı filan bırak da
   hizmetçiler halletsin. Yoksa senin çekirdek, başkalarının hizmetçisi olur.*
**Linus**
   *Hocam, güzel diyorsun da bak [Richard Stallman Abi](https://en.wikipedia.org/wiki/Richard_Stallman) mikro çekirdek yazacam
   diye yıllarını harcadı, saç sakal birbirine karıştı ama hala ortada birşey yok.
   [Emacs](http://www.gnu.org/software/emacs/) bile bitti, çekirdek bitmedi.*
**Tanenbaum Hoca**
   *Bak hala konuşuyor. Dua et benim öğrencim değilsin, yoksa sınıfta kalmıştın.*
</pre></big>

Linus, '*bu akademisyen tayfası adam olmaz*' diye içinden geçirip, bildiği gibi
yoluna devam etmiş. Sonunda ortaya oldukça yetenekli ve hızlı bir çekirdek
çıkmış. GNU araçları ile de bu çekirdeği birleştirince GNU/Linux işletim
sistemi doğmuş. Bu işletim sistemi çok tutmuş, her yerde kullanılmaya
başlanmış.
