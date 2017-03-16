SKYDOG 2016: CATCH ME IF YOU CAN VULNHUB WALKTHROUGH

Bu CTF için verilen 8 Flag için çözümler şöyle olacaktır;

Bir bağlantı taraması yaparak işe başlarsak karşımıza çıkan aynı ağda çalıştırdığımız sanal makinemize bağlantımızı sağlamış bulunuyoruz.

Flag #1 Don’t go Home Frank! There’s a Hex on Your House.

Sanal makinemizde ise root olmamız isteniyor.
![aucc1](https://cloud.githubusercontent.com/assets/26259124/23982564/d3d7ad02-0a16-11e7-91c2-fac06ccf24d3.PNG)

Ipler üzerinde olan web sayfalarını kontrol ettiğimizde ise CTF’in anasayfası karşımıza çıkacaktır.
Sayfamız üzerinde kaynak kodlarını tarattığımızda ise index.html dosyası içerisinde
![aucc2](https://cloud.githubusercontent.com/assets/26259124/23982566/d3d8eb40-0a16-11e7-8167-f0a001f71e13.PNG)
 
Sitede karşıma çıkan ilk sayfa home sayfası olduğu için aklıma CTF’in birinci flagı olan 
“Don’t go Home Frank! There’s a Hex on Your House.”
 Bana bir ipucu verdi. Web sitesinin kaynak koduna bir göz attığımızda ise /oldIE/html5.js dosyası dikkatimi çekti 
 ![aucc3](https://cloud.githubusercontent.com/assets/26259124/23982565/d3d90f12-0a16-11e7-9d87-b9510a86e92d.PNG)

Link olarak tarattığımızda ise karşımıza hex bir şifreleme çıktı.

![aucc4](https://cloud.githubusercontent.com/assets/26259124/23982568/d3dadf86-0a16-11e7-9d5d-1738ebcdc339.PNG)


 
Komut satırımızda ise 

echo 666c61677b37633031333230373061306566373164353432363633653964633166356465657d | -xxd –r –p kodumuzu yazdığımızda karşımıza ilk flagımız çıkıyor 
![aucc5](https://cloud.githubusercontent.com/assets/26259124/23982555/d3a4bc9e-0a16-11e7-942c-179db0b141a7.PNG)
 
Flagımızı encode ettiğimizde ise birçoğumuzun sevdiği tool olan “nmap” ortaya çıkıyor 

FLAG 2

1.Flagda karşımıza çıkan nmap ipucu ile birlikte bir ssh service scan yaptım.
![aucc6](https://cloud.githubusercontent.com/assets/26259124/23982554/d3a3f520-0a16-11e7-804f-347f918be6ee.PNG)



Ve 22222 portuyla bağlantı sağladığımızda ise karşımıza ikinci flagımız çıkıyor 
![aucc7](https://cloud.githubusercontent.com/assets/26259124/23982551/d3a14898-0a16-11e7-8a9f-98701e86c7e2.PNG)
 
Flag{53c82eba31f6d416f331de9162ebe997} 

md5 kodunu decode ettiğimizde ise verilen ipucu “encrypted” olarak görülüyor.




FLAG 3

Flagın adından ve “encrypted”  ipucundan ise site traffiğine bir göz atmak içi SSL sertifikalarına göz atıyoruz.
![aucc 8](https://cloud.githubusercontent.com/assets/26259124/23982550/d3a12606-0a16-11e7-9edb-fd18e508043f.PNG)
 
Ve karşımıza  flag3{f82366a9ddc064585d54e3f78bde3221} çıkıyor. Decode ettiğimizde ise “personnel” ipucu ile karşılaşıyoruz.



FLAG 4
![aucc 11 5](https://cloud.githubusercontent.com/assets/26259124/23982558/d3bc6b46-0a16-11e7-8a68-029287e54adf.png)
Web sayfasında referans yolu gibi görülen bir önceki “personnel” ipucumu denedim. Ve karşıma;

ACCESS DENIED!!! You Do Not Appear To Be Coming From An FBI Workstation. Preparing Interrogation Room 1. Car Batteries Charging....

Gibi bir uyarı yazısı geldi. Erişim engeli olduğunu farkettim. Ufak çaplı yapmış olduğum google aramalarında ise User Agent Switcher 

adlı eklentiyi Mozilla tarayıcı üzerine kurup değişiklikleri yaptım ve karşıma FBI portala benzetilen bir site açıldı ve flagda oradaydı 
  ![aucc10](https://cloud.githubusercontent.com/assets/26259124/23982552/d3a1831c-0a16-11e7-83a9-08f5ece56b5d.PNG)
flag{14e10d570047667f904261e6d08f520f} 

decode: evidence

ve bize verilen flagın altında ise ek bir ipucu var gibi görülüyor.  

Clue=new+flag
 
FLAG 5

Bir önceki flagı bulduğumuzda altında verilen ipucu bize yol gösteriyor. Bulduğumuz flag “evidence” idi. Bizden başına “new” eklememizi istedi.

Yeni kelime “newevidence” olmuş oldu. Web sayfaları arasında oluşturduğumuz bağıntıdan epey hoşlandık ve denemektende çekinmedik. /newevidence yolunu denedik ve karşımıza şöyle bir sonuç geldi.
 
Bir önceki flagı ararken girdiğimiz portal bizi Agent Hanratty olarak gördü. Kim bu Hanratty ismiyle çıktığım google aramalarında ise Hanratty’nin film karakteri olduğu gözüme takıldı. Filmin adı ise Catch Me İf You Can ve Agent Hanratty’nin gerçek adının Carl Hanratty olduğunu öğrendim. Flagın konusunda geçen Dialogue kelimesinden film repliklerine bir göz attım ayrıca user name olarakta hml5.js dosyasının içindeki firstname.secname@blabla bana yardımcı oldu 

Carl Hanratty

User name: carl.hanratty

Password: (Bu kısımda filmin diyalog sahnelerine göz attığımızda gözümüze çarpan anahtar kelimelerin birer kopyasını alarak tek tek 
denediğimde ise “Grace” kelimesinin password olduğunu gördüm  
Giriş başarılı ve “Evidence Summary File” içine girdiğimizde ise bize flagımızı veriyor.
 
Decode flag : panam

FLAG 6 

/newevidence içindeki diğer bağlantılara tıkladığımızda ise bir pdf ve resim gözükmekte.
Resmi indirip biraz incelediğimizde ise boyutunun 4,7 mb olduğunu görüyoruz.

Biraz araştırma sonucu steganografi ile alakalı olduğunu anlıyoruz ve komut satırımızda şu kodları çalıştırıyoruz.
 

Ve bizden bir şifre istiyor bizde ipucumuzu şifremiz olarak kullanmaktan çekinmeyip denediğimiz zaman bize flag.txt adında bir dosya oluşturuyor.
 

Decode flag:IloveFrance

Bulunuyor

FLAG7

Flag isminden anlaşılmak üzere yine bir film konusu olarak replikler içinde dağılmış.
“Hayattaki en hızlı adamım” cümlesinden The Flash isimli film aklıma geliyor.

Flashın gerçek adı Barry Allen ve bir önceki flagdan kalan “iheartbrenda” ipucu belkide bir şifre olabilirler.
Tarama işlemine devam etmek için SSH kullanıyoruz. Ve komut satırında şöyle bir tarama gerçekleştiriyoruz. 

Burada ise bizden password istiyor. Password olarak dikkatmizi bir önceki flagdan ipucu olarak gelen “iheartbrenda” aklımızı karıştırıyor. Denendiğinde ise bağlantı gerçekleşiyor.





Ve bir flag daha gün yüzüne çıkıyor.
 .
Flag encode “theflash” 







FLAG 8

Son flagımızda ipuçlarımız”Frank aklını kaybetti ve kendini binaya kilitledi. Kendini öldürmeden kapının kodunu açın ve “theflash” 

Barry’nin dizinlerine bakarken system-data.zip adlı bir dosya dikkat çekiyor. Bilgisayarıma kopyalayıp unzip ettiğimde ise boyutu 1 GB’ a kadar ulaşıyor. 

Dosyayı çalıştırdığımızda ise bellek dosyalarıyla karşılaşmaktayız.

Verilen bazı ipuçları sayesinde dosyanın bir bellek dökümanı olduğu görülüyor.

Bu bellek dökümünü Volatility Freamwork yardımıyla listeliyoruz 

Bu dosyalar içinde ise notepad.exe bariz bir şekilde gözümüze batarken çalıştırmak için terminale şöyle bir komut bırakıyoruz
 


Açıldıktan sonra code.txt adlı dosyayı görüntülüyoruz
 

Karşımıza bir HEX şifresi çıktı.

Hex	66 6c 61 67 7b 38 34 31 64 64 33 64 62 32 39 62 30 66 62 62 64 38 39 63 37 62 35 62 65 37 36 38 63 64 63 38 31 7d
Flag	flag{841dd3db29b0fbbd89c7b5be768cdc81}
 FLAG DECODED: Two[space]little[space]mice
