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


### Sessizlik
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


### Özgür İrade, Aslında Bir Yanılsama mı
"*Hayatımızı reklamlar yönetiyor*" derlerdi de inanmazdım. İnsanın aklı vardı,
neden duyduğu bir şeyden bu kadar etkilensindi ki... Ama geldiğim duruma bakar
mısınız? Reklam kuşağından kurtulacam derken farkında olmadan Pavlov'un
köpeğine dönmüştüm. Reklam başlayınca otomatik olarak kısayola tıklıyordum.

Bu insanlık dışı durumdan kurtulmam gerekiyordu. Özgürlüğümü yeniden
kazanabilmek için daha çok bilgi sahibi olmalı ve öğrendiklerimi eyleme
dökmeliydim. Yeniden araştırmaya başladım.

```mplayer``` çıktılarını inceleyince kanalın, yapılan yayınla ilgili bazı
bilgiler gönderdiğini gördüm. mplayer çalışırken şu şekilde çıktılar geliyordu:

```bash
ICY Info: StreamTitle='"YASMIN_LE - "NO TENGO';StreamUrl='&artist=
A:1464.9 (24:24.8) of 0.0 (unknown)  0.8% 40%
ICY Info: StreamTitle='"","Title" - V1","Code"';StreamUrl='&artist=
A:1479.3 (24:39.2) of 0.0 (unknown)  0.8% 40%
ICY Info: StreamTitle='"SAM_SMITH - RITING'S O';StreamUrl='&artist=
A:1751.3 (29:11.3) of 0.0 (unknown)  0.8% 40
ICY Info: StreamTitle='"Reklam","","":';StreamUrl='&artist
A:2003.0 (33:23.0) of 0.0 (unknown)  0.8% 40%
```

Çıktıdan da görüleceği gibi **StreamTitle** kısmında yayınlanacak şarkı ile
ilgili bazı bilgiler vardı. Reklam başlayacağı zaman da bu kısımda **Reklam**
yazıyordu. Reklam yazısını gördüğüm anda ```mute``` komutunu otomatik
tetikletirsem artık özgürdüm.


### Konsolun Kalbine Giden Yol, Borudan Geçer
Konsolla aranız iyi ise ```|``` (yani pipe, Türkçe'siyle boru) ile herhangi bir
komutun çıktısını, başka bir komuta girdi olarak gönderebileceğinizi
biliyorsunuzdur. ```mplayer``` çıktısını bir ```while``` döngüsüne
yönlendirilsem ve bu döngü içinde bazı kontroller yapıp uygun anda ```mute```
komutunu tetiklersem bu iş olabilirdi. Komutu hazırladım:

```bash
mplayer -quiet -slave -input file=/tmp/mplayer.pipe http://46.20.7.104/ | \
while read line
do
    echo $line
    [ "$(echo $line | grep -v StreamTitle)" ] && continue

    title=$(echo $line | cut -d '"' -f2)
    [ -z "$title" ] && continue
    [ "$title" = "Reklam" ] && echo mute > /tmp/mplayer.pipe
done
```

```mplayer``` çıktılarını alan ```while``` döngüsü kısaca şunu yapıyordu:

* Satırda **StreamTitle** kelimesi geçmiyorsa bu satırla bir işi olmadığında
bir sonraki satıra atlıyordu.

* **StreamTitle** kelimesi geçiyorsa şarkı adını alıyordu.

* Şarkı adı belirlenemediyse (bazen boş geliyor) bir sonraki satıra atlıyordu.

* Şarkı adı olarak **Reklam** yazıyorsa sesi kapatıyordu.


### Obsesyon (Takıntı)
Israrlı bir şekilde sürekli aklımıza gelen, bir türlü engel olamadığımız,
beynimizi bir tahta kurdu gibi sürekli kemiren sinir bozucu düşünce...

Yapılan klinik deneyler, düzgün çalışmayan yazılımların obsesyona sebep
olduğunu ve yazılımcıların %93.27'sinin sinir bozucu (amiyane tabirle gıcık)
olduğunu göstermekte... Bu son örnek de bunu doğruluyordu.

Reklam başlayınca, ses otomatik olarak kapatılıyordu ama reklam bitince
otomatik açılmıyordu. Reklamın bittiğini farkedip manuel olarak sesi açmak
gerekiyordu. Dolayısı ile ses kapatıldıktan bir süre sonra beynimi, "*acaba
reklam bitmiş midir, sesi artık açsam mı*" gibi sinir bozucu düşünceler
kaplıyordu. Bir yazılımcı olarak kendi sinirlerimi de bozmayı başarmıştım.

Komutu biraz düzenlemem gerekiyordu. Reklam bittiği zaman da sesi otomatik
olarak açtıracaktım. Yalnız dikkat edilmesi gereken bir nokta vardı: ses zaten
kapalıyken sesi kapatmaya, ses zaten açıkken de sesi açmaya kalkmamalıydım.
Yoksa her tetiklendiğinde modu tersine çeviren (yani **on** ise **off**,
**off** ise **on** yapan) ```mute``` komutu, yanlış çalışacaktı. Dolayısı ile
```mute``` durumunu takip etmek gerekiyordu.

Komut artık şu şekli almıştı:

```bash
MUTE=false
[ -e /tmp/mplayer.pipe ] || mkfifo /tmp/mplayer.pipe

mplayer -quiet -slave -input file=/tmp/mplayer.pipe http://46.20.7.104/ | \
while read line
do
    echo $line;
    [ "$(echo $line | grep -v StreamTitle)" ] && continue

    title=$(echo $line | cut -d '"' -f2)
    [ -z "$title" ] && continue

    if [ "$title" = "Reklam" ]
    then
        $MUTE || echo mute > /tmp/mplayer.pipe
        MUTE=true
    else
        $MUTE && echo mute > /tmp/mplayer.pipe
        MUTE=false
    fi
done
```

Değişen kısımlar:

* Named pipe (/tmp/mplayer.pipe) henüz oluşturulmamışsa ```mkfifo``` ile
oluştur.

* Reklam kelimesi yakalandıysa ve mute modunda değilse, sesi kapat.

* Bir şarkı adı yakalandıysa ve mute modunda ise sesi aç.


### Fiber Internet
Reklamları bir türlü anlayamıyorum. Mesela bi tane firma var, "*fiber
Internet*" diye garip bir şeyin reklamını yapıyor. Reklamı yapıldığı için ben
de satılan bir şey sandım, "*şundan eve alalım*" dedim. Firma ile görüştüm ama
bizim eve getiremiyorlarmış, bize satmadılar. Halbuki sokağın başındaki laz
bakkal, avokado bile getiriyor. Avokadonun bile gelebildiği bir yere, fiber
Internet nasıl gelemiyor anlamadım.

Bizim iş yeri de o şeyden satın almak istemiş ama onlara da satmamışlar. O
nedenle Internet bağlantım, über süper değil. Über süper bir bağlantı olmayınca
sanırım ```mplayer```, müziği kesintisiz verebilmek için buffer kullanıyor.
Buffer olunca da gelen bilgi ve müzik arasında bir süre farkı oluyor. Yani
**Reklam** bilgisi geldikten 5-6 saniye sonra reklam başlıyor. Oysa ki ben
komutu, 21.  yüzyılda çalışacak şekilde tasarlamıştım ve gecikme olacağını
hesaba katmamıştım.

Durum böyle olunca İlber Ortaylı Hoca'ya hemen bi telgraf gönderdim. "*Osmanlı
döneminde Internet kullanımı*" ile ilgili temel bilgileri aldıktan sonra bu
gecikmeyi de hesaba katacak şekilde komutu düzenledim. Artık komut şu hale
gelmişti:

```bash
MUTE=false
WAIT=5
echo $WAIT > /tmp/mpwait
[ -e /tmp/mplayer.pipe ] || mkfifo /tmp/mplayer.pipe

mplayer -quiet -slave -input file=/tmp/mplayer.pipe http://46.20.7.104/ | \
while read line
do
    echo $line;
    [ "$(echo $line | grep -v StreamTitle)" ] && continue

    title=$(echo $line | cut -d '"' -f2)
    [ -z "$title" ] && continue

    if [ "$title" = "Reklam" ]
    then
        $MUTE || (sleep $(cat /tmp/mpwait); echo mute > /tmp/mplayer.pipe) &
        MUTE=true
    else
        $MUTE && (sleep $(cat /tmp/mpwait); echo mute > /tmp/mplayer.pipe) &
        MUTE=false
    fi
done
```

Bu seferki farklar:
* Gecikme süresi, komut çalışırken istenirse değiştirilebilsin diye,
/tmp/mpwait dosyasına kaydediliyor.

* Ses açılıp kapatılacağı zaman bu gecikme süresi kadar beklenip ondan sonra
mute komutu tetikleniyor.


### Mutlu Son
Sonunda istediğim olmuştu. Artık rahat bir şekilde müzik dinliyebiliyordum ama
kafama takılan bir şey vardı: o mucize şampuandan ben de almalı mıydım?
