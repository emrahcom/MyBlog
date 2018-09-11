Müziğe Evet, Yağlı Saçlara Hayır
================================

### Aydınlanma
Her şey, yeni bir eve taşınmamla başladı. Önceden iş yerine varmam 5 dakika
sürüyordu. Bu süre, bir anda 45 dakikaya çıkınca aydınlanma yaşadım ve bazı
insanların neden müzik olmadan yapamadığını anladım: bu yol (ve bazen de
hayat), başka türlü çekilecek gibi değildi.

Aydınlanma sürecim, daha önce anlam veremedim bir çok şeyi de anlamamı sağladı.
Örneğin "*yolu bilmek ile yolda gitmek*" aynı şey değildi. Bu koduğumun yolu,
git git bi türlü bitmiyordu ama yolu bilmek için Google Map'e bakmak
yeterliydi. Ayrıca o bilgenin, Ferrari'sini neden sattığını da artık çok iyi
anlamıştım.

Neyse, bu yeni hayatımda artık müziğe daha çok yer verecektim. İşyerinde
bilgisayar ile çalışırken de radyo dinlemeye karar verdim ve yoldayken
dinlediğim [Radio Slow Time](http://slowtime.com.tr/)'ın Internet üzerinden
yaptığı yayını buldum. Artık bilgisayar başına oturunca bir konsol açıyor ve
şu komutu çalıştırıyordum:

```bash
mplayer http://46.20.7.104/
```

Ama hayat bu kadar basit değildi ve yeni zorluklar beni bekliyordu.


### Yağlı Saçlar
İnsanlığın en büyük sorunu ile yüzleşmem de bu vesile ile oldu.
[Radio Slow Time](http://slowtime.com.tr/), reklam kuşaklarında çağımızın
vebası "*yağlı saçlar*" konusunda bilinçlendirici yayınlar yapıyor, bunun bir
son olmadığını, hala bir umut olduğunu anlatıyordu.

Önceleri çok önemsemedim. "*İnsanlar, o mucize şampuanı nasıl olsa alır, yağlı
saçlar sorunu da kısa sürede çözülür*" diye düşündüm ama cahil halkımız, her
zamanki tavrı ile bu sorunu da görmezden geldi. Israrla o mucize şampuanı
almadılar.

Artık önümde iki seçenek kalmıştı. Ya o mucize şampuanı ben alıp milletin yağlı
saçlarını zorla yıkayacaktım ya da reklam kuşağı başladığında mplayer'ın sesini
kısacaktım. Birinci yöntem bana pek pratik görünmedi.


# Sessizlik
```mplayer```'ın sesini kapatmak için işimi yarım bırakıp ```mplayer```'ın açık
olduğu masaüstüne geçmek, sesi kapatmak ve tekrar çalıştığım masaüstüne dönmek
iyi bir çözüm değildi. Bir kısayolla bu işi halletmem gerekiyordu.

Biraz araştırma yapınca ```mplayer```'da slave mod diye bir şey olduğunu
öğrendim. Slave moddayken ```mplayer```, **input** noktasına gönderilen
komutları algılıyor ve gerekli işlemi yapıyordu. Yani artık ```mplayer```'ı şu
şekilde başlatacaktım:

```bash
mkfifo /tmp/mplayer.pipe
mplayer -slave -input file=/tmp/mplayer.pipe http://46.20.7.104/
```

Bu komutu, bir kısayola bağlayınca düşündüğüm oldu ama hala yolunda gitmeyen
bir şeyler vardı.
