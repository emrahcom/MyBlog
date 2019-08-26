10 dakika 7 saniyede kendi Github sunucumuzu kurmak
===================================================

"*21 Günde Python Öğrenin*" veya "*24 Saatte Java*" gibi kitapları
görmüşsünüzdür ve sonuç, hiç de kitabın adında yazdığı gibi olmaz. Bu başlıkta
yazan da aslında doğru değil ama bir farkla: zaman kısmı doğru, GitHub kısmı
yanlış... Aslında GitHub değil, web arayüzü GitHub'a çok benzeyen, kendi Git
sunucumuzu kuruyoruz.

Saat tutup denedim ve gerçekten de **10 dakika 7 saniye** sürdü. Ve daha da
güzeli, bütün yapacağımız, sadece 2 komut yazıp basit bir web formunu
doldurmak...


### Arkada ne dolaplar dönüyor
Birazdan yazacağım birkaç basit komutu çalıştırdığınızda, arkaplanda şunlar
gerçekleşecek:

* host makinede, dışarıya kapalı sanal bir network oluşturulacak

* bir Linux container (LXC) oluşturulacak ve ayarlanacak

* veritabanı sunucusu kurulacak

* Reverse proxy olarak çalışacak bir Nginx sunucu kurulacak ve ayarlanacak

* Git sunucu kurulacak

* nftables ile NAT ayarları yapılacak

* Self signed SSL sertifikası oluşturulacak

* vs vs vs

Bütün bunlarla uğraşmak istemiyorsanız, doğru yere geldiniz ama "*Yok, ben illa
arıza çıkaracağım. Olayın detaylarını da öğrenmek istiyorum*" derseniz,
[kaynak kodlar](https://github.com/emrahcom/emrah-stretch) açık...
Dilediğiniz gibi inceleyebilirsiniz. Takıldığınız yer olursa bana email atın.


### Ama bir şartım var
Bu işi yapabilmek için tek bir şey gerekiyor:
[Debian Stretch](https://www.debian.org/) kurulu bir makine...

"*Ya şimdi kim uğraşacak Debian kurmakla*" diyorsanız, bulut hizmeti veren bir
yerden hazır kurulu bir [Debian Stretch](https://www.debian.org/) makine
kiralayabilirsiniz. Bu tip işler için ben genellikle
[Digital Ocean](https://www.digitalocean.com/?refcode=92b0165840d8)'ı tercih
ediyorum.

"*Yok ben yine arıza çıkaracağım. Bulutsuz olmaz mı*" diyorsanız, sanal
makineye, Debian Stretch kurup deneyebilirsin. Yalnız (swap dahil) minimum 1 GB
RAM ayırmanız gerekiyor ve (i386 değil) AMD64 mimarisini kullanmalısınız.


### Lafı daha fazla uzatmayayım
Şimdi sıra geldi mucizevi komutlarımıza... Debian Stretch makineye **root**
olarak bağlandıktan sonra şu 2 komutu veriyoruz:

```bash
wget https://raw.githubusercontent.com/emrahcom/emrah-stretch/master/installer/es
bash es es-gogs
```

Birinci komut, kurulumu yapacak olan Bash scripti indiriyor. İkinci komut ise
kurulumu yapıyor. Script işini bitirdikten sonra web tarayıcımızı açıp IP
adresini kullanarak sunucuya bağlanıyoruz. Açılan formda sadece 2 yeri
değiştirmeniz gerekiyor: **Domain** ve **Application URL**

Eğer bu sunucu için bir alan adı kullanmayacaksanız, "*your.domain.name*" yazan
yerlere, sunucunun IP adresini yazabilirsiniz. Bu kadar...


### Güncelleme
_2019-08-26_ - [Debian](https://www.debian.org/) yeni sürümünü yayınladı.
[Debian Buster](https://www.debian.org/) makineye kurulum yapacaksanız artık şu
komutları kullanınız:

```bash
wget https://raw.githubusercontent.com/emrahcom/emrah-buster-base/master/installer/eb
wget https://raw.githubusercontent.com/emrahcom/emrah-buster-templates/master/installer/eb-gitea.conf
bash eb eb-gitea
```

Bu yeni sürümde [Gogs](https://gogs.io/) değil, [Gitea](https://gitea.io/en-us/)
kullandım. [Gogs](https://gogs.io/)'dan klonlanan yeni bir proje...
