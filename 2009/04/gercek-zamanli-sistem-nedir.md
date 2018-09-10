Gerçek zamanlı (real-time) sistem nedir?
========================================
İşlerini, tam zamanında yapan sisteme, gerçek zamanlı sistem denir. Dolayısı
ile tam zamanında yapılması gereken işlerimiz yoksa, gerçek zamanlı bir sisteme
de ihtiyacımız yok demektir.

Bir işin, tam zamanında yapılması gerekiyorsa bu iş, zaman açısından kritik bir
iştir. Zaman açısından kritik işler, zamanında yapılamazlarsa başarısızlıkla
sonuçlanmış olurlar.

Örneğin yemek pişirmek, zaman açısından kritik bir iştir. Bir yemek, olması
gerekenden az veya çok pişirilirse, başarısızlıkla sonuçlanmış demektir.
Dolayısı ile iyi aşçılar, gerçek zamanlı çalışan organik sistemlerdir.

Yalnız bu tanımda dikkat edilmesi gereken bir şey daha vardır. O da **tam
zamanında** ifadesi ile kastedilen işin bitirilme anının, aslında akıp giden
zaman içinde bir anı değil, bir süreyi ifade ettiğidir.

180°'de 45 dakika pişmesi gereken levrek buğulamayı, 44. dakikada veya 46.
dakikada fırından çıkarırsak aslında hatalı birşey yapmış olmayız çünkü bu ufak
sapma, kabul edilebilir düzeydedir ve kimse kalkıp da '*bu yemek iyi pişmemiş*'
demez. Eğer yemeği yapan, işinin ehli bir aşçı ise yemeğin, çiğ veya yanık
şekilde önümüze gelmeyeceğini biliriz.

Gerçek zamanlı sistemler, **latency** terimi ile ifade edilen bu sapmaların,
belli bir değerden küçük olacağını bize garanti ederler.


###Soft Real-time ve Hard Real-time
Aşçı denilen organizmaların, yemeklerin pişirilme süreleri konusunda ne kadar
hassas sistemler olduğuna değinmiştik. Peki ama aşçılar hiç mi hata yapmaz? Bir
aşçı, arada bir hata yapıp yemeği hafif yaksa ne olur?

Ne olacağı, bu aşçının yemeklerini kimin yediğine bağlıdır. Eğer Sirkeci'de bir
lokantada çalışıyorsa (ki burada kasdedilen Konyalı'nın aşçıları değildir)
hafif yanık yemeği müşteriye kakalarsın gider, en kötü ihtimal o müşteri, bir
daha lokantaya uğramaz. Yani çok da dert değil, müşterinin suyu mu çıktı? Bu
gelmezse öbürü gelir.

Eğer söz konusu aşçımız, sarayın aşçıbaşısı ise ve yemeklerini yiyen padişah
ise, işte o zaman durum kritiktir, hayati bir durum söz konusudur. Artık aşçıya
reset mi atarlar, kazığa oturtup Youtube'da videosunu mu yayınlarlar
bilemiyorum.

Birinci aşçı organizması, **soft real-time** sisteme; ikinci aşçı organizması,
**hard real-time** sisteme örnektir.

İşlerimizi, belli bir sapmayı aşmayacak şekilde yapacağını bize garanti eden
sistemimiz, arada sırada bu sözünü yerine getiremiyor ama bu kusurun, göz ardı
edilebilir sonuçları oluyorsa, söz konusu sistem **soft real-time**'dır.

Sistemimiz, garanti edilen sapma aralığının asla ve asla dışına çıkmıyorsa ve
bu sistemde çalışan işler, sapma aralığının dışına çıkıldığında kabul edilemez
sonuçlar doğuruyorsa, sistemimiz **hard real-time**'dır.


###Jitter
Aşçıların bir tipi vardır ki buna da jitter denir. Mutfak havalandırmasının iyi
olmamasından dolayı sürekli buhar altında kalan ve yamaklığı sırasında her gün
zorla üç çuval patates soydurulan aşçılar arasında sıklıkla bu tipe rastlanır.
Jitter'lar yemeği, bazen az pişmiş bırakır, bazen hafiften yakarlar. Ama bazen
de bakarsın en mükemmel yemekle çıkıp gelirler.

Bu tip aşçılar lokanta sahipleri tarafından pek sevilmez ve istenmezler çünkü
müşteriyi kaçırırlar. Yemeği hep pişkin yapsa sorun değil, o zaman en azından
pişkin yemek seven müşteriler sürekli gelir. Sürekli az pişmiş bıraksa da sorun
değil, o zaman da az pişmiş yemek seven müşterilerle idare edilir. Mutfaktan ne
çıkacağı belli olmayınca, müşterinin hiçbir türü kalmaz.

Bu nedenle gerçek zamanlı sistemlerde jitter sevilmez. Sapma olacaksa bile (ki
mutlaka olur, bu sadece ne kadar hassas ölçüm yaptığımıza bağlıdır) en azından
sapmaların hep aynı yönde ve benzer oranlarda olması istenir; tabii garanti
edilen aralığı da aşmamak koşulu ile...


###Gerçek zamanlı sistem hızlı mı olmalı?
Aşçımız, evde çocuklarına yemek pişiren bir anne ise hızlı olmasına gerek
yoktur, üç tencereyi kontrol altında tutabilmesi yeterlidir. Ama onlarca
yemeğin aynı anda hazırlanması gereken bir lokanta söz konusu ise bunca yemeği
aynı anda kontrol edebilecek ve hepsinin tam kıvamında pişmesini sağlayabilecek
hızlı bir aşçıya ihtiyaç vardır.

Tabii aşçının hızlı olması, yemekleri tam kıvamında pişireceğinin garantisi
değildir. Ama aynı zamanda, beş kap yemeği tam kıvamında pişirebilen bir
aşçının, yeterince hızlı değilse on kap yemeği tam kıvamında pişireceği de
garanti değildir.

Gerçek zamanlı sistemler, kaldırabileceği oranda iş yükleri varsa gerçek
zamanlı olma özelliklerini koruyabilirler. Dolayısı ile gerçek zamanlı bir
sistem kurgulanırken iş yükü, baştan kesin bir doğrulukla hesaplanmalıdır.


###Gerçek zamanlı sistemde tampon (buffer) kullanımı
Börekçiler tampon ile çalışır. Bi sabah börekçiye gidip '*peynirli var mı*'
diye sorulduğunda '*10 dakika sonra hazır*' cevabı alınabilirken, ertesi gün
tezgahın üzerinde tonlarca peynirli börek bulunabilir. Dolayısı ile '*bugün
kesin peynirli börek yiyecem*' diye börekçiye gidip oturduğumuzda böreğin ne
zaman önünüze geleceğinden asla emin olamayız. Bu nedenle hard real-time
sistemlerde tampon kullanılmaz.


###Pre-emptive nedir?
Aile terbiyesi almamış aşçıya, pre-emptive denir. Bu aşçı tipi, yemeklerine
özen göstermez, kimini yakar, kimini çiğ bırakır. Yemek diye çiğ tavuk sunduğu
bile görülmüştür ama ne zaman ki kapıdan yağlı bir müşteri girer, hemen Oktay
Usta kesilir. Bu müşterinin yemeklerine özel bir hassasiyet gösterir, mükemmel
olması için gayret eder. Tabii bu tip bir aşçı bozuntusunun ne derece
mükemmel(!) iş yapacağı malumunuz. O nedenle hard real-time dünyasında yeri
yoktur, adam yerine konulmaz.

Bu yazıdan çıkarılacak sonuca gelirsek, son söz olarak şunu diyebiliriz:
'*Hamburger yemeyin*'
