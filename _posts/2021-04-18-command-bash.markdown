---
layout: b-post
title:  "command Komutu"
modified: 2021-04-16
author: Taylan Özgür Bildik
excerpt: "Bash kabuğunda yerleşik olarak bulunan builtin komutunun kullanım açıklamasıdır."
tags: [bash, bash builtin, yerleşik bash komutları]
categories: blog
---

Bash üzerinde kullanılabilir olan komutlar(yani programlar-araçlar) ile aynı ada sahip takma isim(`alias`) ya da fonksiyon tanımlaması yapıldıysa, `command` komutu kullanıldığında aynı isme ada sahip takma isim ve fonksiyonlar görmezden gelinerek orijinal komut çalıştırılır. Çünkü `command` komutu, kendisine argüman olarak verilmiş olan ifadeyi öncelikli olarak komutların dizin adreslerini tutan **PATH** yolu üzerinde arar. Hemen denemek için öncelikle `ls` komutu ile aynı ada sahip bir takma ad (`alias`) tanımlaması yapıp `ls` komutunu konsola girmeyi deneyelim.

```bash
taylan@taylan:~$ alias ls="echo 'ben ls komutunun yerine alan takma adım'"
taylan@taylan:~$ ls
ben ls komutunun yerine alan takma adım
taylan@taylan:~$
```

Görebildiğiniz gibi takma ad gerçek `ls` komutunu domine ediyor. Eğer böyle bir durumda `ls` komutunu kullanmak istersek `command ls` komutunu kullanmamız yeterli.

```bash
taylan@taylan:~$ ls
ben ls komutunun yerine alan takma adım
taylan@taylan:~$ command ls
Belgeler  Downloads  Genel  Masaüstü  Müzik  Resimler  skel  Şablonlar  Videolar
taylan@taylan:~$
```

Aynı durumu fonksiyonlar üzerinden de gözlemleyebiliriz. 

```bash
taylan@taylan:~$ function cd {
> echo "ben 'cd' komutunun yerini alan fonksiyonum"
> }
taylan@taylan:~$
taylan@taylan:~$ cd /home/
ben 'cd' komutunun yerini alan fonksiyonum
taylan@taylan:~$ command cd /home/
taylan@taylan:/home$
```

Ayrıca `command` komutunun birkaç seçeneği de bulunuyor. 

# Seçenekler

## p seçeneği;

Örneğin `command` komutunun kendisine argüman olarak verilen ifadeyi **PATH** yolu üzerinde aradığını söylemiştik. **PATH** yolu kullanıcının istekleri doğrultusunda düzenlenebiliyor yani varsayılan olarak belirlenmiş olan **PATH** yolu değiştirme imkanımız da var. Eğer biz `command` komutunun yalnızca **varsayılan PATH yolunu** kullanmasını istersek `-p` seçeneğini kullanabiliriz. Denemek için ev dizinimizde betik dosyası oluşturup, ev dizinimizi de PATH yoluna ekleyelim. Daha sonra PATH yoluna ekli olan betik dosyasına yetki verip, ismi ile konsol üzerinden çalıştıralım.

```bash
taylan@taylan:~$ cat > betik.sh
echo "ben bir betik dosyasıyım ve çalıştım !"
taylan@taylan:~$ chmod +x betik.sh
taylan@taylan:~$ export PATH="/home/taylan/":$PATH
taylan@taylan:~$ echo $PATH
/home/taylan/:/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
taylan@taylan:~$ betik.sh
ben bir betik dosyasıyım ve çalıştım !
taylan@taylan:~$ 
```

Betik dosyamızın PATH yoluna eklediğimiz dizin konumu sayesinde konsol üzerinden ismi ile çalıştığını teyit ettik. Eğer biz PATH yolu üzerinde yapılmış olan değişikler harici **varsayılan PATH** yolu üzerindeki komutlar kullanılsın istersek `command` komutunun `p` seçeneğini kullanabiliriz. Fakat bu seçeneğin doğru çalışabilmesi `hash` değerinin `hash -r` komutu ile silinmesi gerekiyor. Çünkü betik dosyası daha önce teyit edilmek için çalıştırıldığından hash değeri kayıt altına alınıyor ve varsayılan PATH yolundan önce hash değeri üzerinden betik.sh dosyası, konumunda bulunup çalıştırılıyor. Bu sebeple eğer betik dosyasını daha önce çalıştırdıysak `hash -r` komutu ile silmemiz gerekir. Eğer hash konusunda kafanız karıştıysa ayrıca hash yapısının açıklamasına göz atabilirsiniz.

```bash
taylan@taylan:~$ cat > betik.sh
echo "ben bir betik dosyasıyım ve çalıştım !"
taylan@taylan:~$ hash -r 
taylan@taylan:~$ command -p betik.sh
bash: betik.sh: komut yok
taylan@taylan:~$ command betik.sh 
Ben betik dosyasıyım ve çalıştım :)
taylan@taylan:~$ betik.sh 
Ben betik dosyasıyım ve çalıştım :)
```

## v seçeneği;

Bu seçenek argüman olarak belirtilmiş olan komut hakkında kısaca `type` komutu gibi bilgi sunar.

```bash
taylan@taylan:~$ command -v ls
alias ls='ls --color=auto'
taylan@taylan:~$ type ls
ls `ls --color=auto' için takma addır
```

## V seçeneği;

Bu seçenek argüman olarak belirtilmiş olan komut hakkında `type` komutu gibi bilgi sunar.