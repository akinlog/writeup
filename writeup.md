SKYDOG 2016: CATCH ME IF YOU CAN VULNHUB WALKTHROUGH



Sanal makinemizi ve Kali Linux makinemizi  Oracle VirtualBox ile ayaklandırdıktan sonra ilk iş olarak ağımdaki hedef sistemde bir port taraması yapıyoruz

Flag #1 Don’t go Home Frank! There’s a Hex on Your House.

Sanal makinemizde ise root olmamız isteniyor.
![aucc4](https://cloud.githubusercontent.com/assets/26259124/24017186/b4fa8ec8-0a97-11e7-9c95-3eabfd3e1eed.PNG)

Ipler üzerinde olan web sayfalarını kontrol ettiğimizde ise CTF’in anasayfası karşımıza çıkacaktır.
Sayfamız üzerinde kaynak kodlarını tarattığımızda ise index.html dosyası içerisinde
![aucc3](https://cloud.githubusercontent.com/assets/26259124/24017187/b50ff592-0a97-11e7-9d73-41eec4612a23.PNG)

 
Sitede karşıma çıkan ilk sayfa home sayfası olduğu için aklıma CTF’in birinci flagı olan 
“Don’t go Home Frank! There’s a Hex on Your House.”
 Bana bir ipucu verdi. Web sitesinin kaynak koduna bir göz attığımızda ise /oldIE/html5.js dosyası dikkatimi çekti 
![aucc6](https://cloud.githubusercontent.com/assets/26259124/24017201/b557572a-0a97-11e7-89d8-9991115a527a.PNG)

Link olarak tarattığımızda ise karşımıza hex bir şifreleme çıktı.


![aucc7](https://cloud.githubusercontent.com/assets/26259124/24017203/b55f9c14-0a97-11e7-8cbd-719f7940595d.PNG)
 
Komut satırımızda ise 

echo 666c61677b37633031333230373061306566373164353432363633653964633166356465657d | -xxd –r –p kodumuzu yazdığımızda karşımıza ilk flagımız çıkıyor 

 ![aucc 8](https://cloud.githubusercontent.com/assets/26259124/24017197/b5369472-0a97-11e7-9f28-79e6f26962a9.PNG)
Flagımızı encode ettiğimizde ise birçoğumuzun sevdiği tool olan “nmap” ortaya çıkıyor 

FLAG 2

1.Flagda karşımıza çıkan nmap ipucu ile birlikte bir ssh service scan yaptım.
![aucc 9](https://cloud.githubusercontent.com/assets/26259124/24017196/b536043a-0a97-11e7-8ad3-b8153f6cdf91.PNG)



Ve 22222 portuyla bağlantı sağladığımızda ise karşımıza ikinci flagımız çıkıyor 

 ![aucc10](https://cloud.githubusercontent.com/assets/26259124/24017204/b5739aa2-0a97-11e7-922d-6b503a9b7567.PNG)
Flag{53c82eba31f6d416f331de9162ebe997} 

md5 kodunu decode ettiğimizde ise verilen ipucu “encrypted” olarak görülüyor.




FLAG 3

Flagın adından ve “encrypted”  ipucundan ise site traffiğine bir göz atmak içi SSL sertifikalarına göz atıyoruz.

 ![aucc11](https://cloud.githubusercontent.com/assets/26259124/24017200/b5532bd2-0a97-11e7-9ca0-7c4b83353cfa.PNG)

Ve karşımıza  flag3{f82366a9ddc064585d54e3f78bde3221} çıkıyor. Decode ettiğimizde ise “personnel” ipucu ile karşılaşıyoruz.



FLAG 4
Web sayfasında referans yolu gibi görülen bir önceki “personnel” ipucumu denedim. Ve karşıma;
![aucc 11 5](https://cloud.githubusercontent.com/assets/26259124/24017193/b52f7048-0a97-11e7-949e-bd9812fe6f90.png)
ACCESS DENIED!!! You Do Not Appear To Be Coming From An FBI Workstation. Preparing Interrogation Room 1. Car Batteries Charging....

Gibi bir uyarı yazısı geldi. Erişim engeli olduğunu farkettim. Ufak çaplı yapmış olduğum google aramalarında ise User Agent Switcher 

adlı eklentiyi Mozilla tarayıcı üzerine kurup değişiklikleri yaptım ve karşıma FBI portala benzetilen bir site açıldı ve flagda oradaydı 
  ![aucc 12](https://cloud.githubusercontent.com/assets/26259124/24017194/b532b776-0a97-11e7-9b4f-195b674653ef.png)
flag{14e10d570047667f904261e6d08f520f} 

decode: evidence

ve bize verilen flagın altında ise ek bir ipucu var gibi görülüyor.  
![aucc13](https://cloud.githubusercontent.com/assets/26259124/24017202/b55824b6-0a97-11e7-8226-cc70d17c02a6.png)
Clue=new+flag
 
FLAG 5

Bir önceki flagı bulduğumuzda altında verilen ipucu bize yol gösteriyor. Bulduğumuz flag “evidence” idi. Bizden başına “new” eklememizi istedi.

Yeni kelime “newevidence” olmuş oldu. Web sayfaları arasında oluşturduğumuz bağıntıdan epey hoşlandık ve denemektende çekinmedik. /newevidence yolunu denedik ve karşımıza şöyle bir sonuç geldi.
![aucc14](https://cloud.githubusercontent.com/assets/26259124/24017199/b54f9990-0a97-11e7-8c9f-776098a48e48.PNG)
 
Bir önceki flagı ararken girdiğimiz portal bizi Agent Hanratty olarak gördü. Kim bu Hanratty ismiyle çıktığım google aramalarında ise Hanratty’nin film karakteri olduğu gözüme takıldı. Filmin adı ise Catch Me İf You Can ve Agent Hanratty’nin gerçek adının Carl Hanratty olduğunu öğrendim. Flagın konusunda geçen Dialogue kelimesinden film repliklerine bir göz attım ayrıca user name olarakta hml5.js dosyasının içindeki firstname.secname@blabla bana yardımcı oldu 

Carl Hanratty

User name: carl.hanratty

Password: (Bu kısımda filmin diyalog sahnelerine göz attığımızda gözümüze çarpan anahtar kelimelerin birer kopyasını alarak tek tek 
denediğimde ise “Grace” kelimesinin password olduğunu gördüm  
![aucc 15](https://cloud.githubusercontent.com/assets/26259124/24017192/b51a3b1a-0a97-11e7-9ba2-dfcb4107bb96.PNG)
Giriş başarılı ve “Evidence Summary File” içine girdiğimizde ise bize flagımızı veriyor.
![aucc 16](https://cloud.githubusercontent.com/assets/26259124/24017190/b514e3b8-0a97-11e7-95ff-8126740fd856.PNG)
 
Decode flag : panam

FLAG 6 

/newevidence içindeki diğer bağlantılara tıkladığımızda ise bir pdf ve resim gözükmekte.
Resmi indirip biraz incelediğimizde ise boyutunun 4,7 mb olduğunu görüyoruz.

Biraz araştırma sonucu steganografi ile alakalı olduğunu anlıyoruz ve komut satırımızda şu kodları çalıştırıyoruz.
![aucc17](https://cloud.githubusercontent.com/assets/26259124/24017198/b53cc086-0a97-11e7-9c69-95b6469f3b77.PNG) 

Ve bizden bir şifre istiyor bizde ipucumuzu şifremiz olarak kullanmaktan çekinmeyip denediğimiz zaman bize flag.txt adında bir dosya oluşturuyor.
 
![image](https://cloud.githubusercontent.com/assets/26259124/24017678/9dca86ca-0a99-11e7-8ebe-3e51828055e1.png)

Decode flag:IloveFrance

Bulunuyor

FLAG7

Flag isminden anlaşılmak üzere yine bir film konusu olarak replikler içinde dağılmış.
“Hayattaki en hızlı adamım” cümlesinden The Flash isimli film aklıma geliyor.

Flashın gerçek adı Barry Allen ve bir önceki flagdan kalan “iheartbrenda” ipucu belkide bir şifre olabilirler.
Tarama işlemine devam etmek için SSH kullanıyoruz. Ve komut satırında şöyle bir tarama gerçekleştiriyoruz. 

![image](https://cloud.githubusercontent.com/assets/26259124/24017693/ace0c836-0a99-11e7-8631-6e0eea486c84.png)

Burada ise bizden password istiyor. Password olarak dikkatmizi bir önceki flagdan ipucu olarak gelen “iheartbrenda” aklımızı karıştırıyor. Denendiğinde ise bağlantı gerçekleşiyor.





Ve bir flag daha gün yüzüne çıkıyor.
 
 ![image](https://cloud.githubusercontent.com/assets/26259124/24017709/bc5f75a0-0a99-11e7-97e8-aec238d3c90e.png)

Flag encode “theflash” 







FLAG 8

Son flagımızda ipuçlarımız”Frank aklını kaybetti ve kendini binaya kilitledi. Kendini öldürmeden kapının kodunu açın ve “theflash” 

Barry’nin dizinlerine bakarken system-data.zip adlı bir dosya dikkat çekiyor. Bilgisayarıma kopyalayıp unzip ettiğimde ise boyutu 1 GB’ a kadar ulaşıyor. 

![image](https://cloud.githubusercontent.com/assets/26259124/24017722/cf5604f8-0a99-11e7-959a-e63f4bf02918.png)

Dosyayı çalıştırdığımızda ise bellek dosyalarıyla karşılaşmaktayız.

Verilen bazı ipuçları sayesinde dosyanın bir bellek dökümanı olduğu görülüyor.

Bu bellek dökümünü Volatility Freamwork yardımıyla listeliyoruz 

![image](https://cloud.githubusercontent.com/assets/26259124/24017736/d92cd9d4-0a99-11e7-8247-c3cb729689f6.png)


Bu dosyalar içinde ise notepad.exe bariz bir şekilde gözümüze batarken çalıştırmak için terminale şöyle bir komut bırakıyoruz
 
![image](https://cloud.githubusercontent.com/assets/26259124/24017745/e07d5ea2-0a99-11e7-9825-0d0dbffe1df2.png)





Açıldıktan sonra code.txt adlı dosyayı görüntülüyoruz
![image](https://cloud.githubusercontent.com/assets/26259124/24017752/ea72b3bc-0a99-11e7-9832-754b5e8271cf.png)

 

Karşımıza bir HEX şifresi çıktı.

Hex	66 6c 61 67 7b 38 34 31 64 64 33 64 62 32 39 62 30 66 62 62 64 38 39 63 37 62 35 62 65 37 36 38 63 64 63 38 31 7d
Flag	flag{841dd3db29b0fbbd89c7b5be768cdc81}
 FLAG DECODED: Two[space]little[space]mice
