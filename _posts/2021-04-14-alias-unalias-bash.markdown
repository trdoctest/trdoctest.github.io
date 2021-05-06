---
layout: post
title:  "alias ve unalias Komutu"
author: Taylan Özgür Bildik
modified: 2021-04-14
excerpt: "Bash kabuğunda yerleşik olarak bulunan alias ve unalias komutlarının açıklamasıdır."
tags: [bash, bash builtin, yerleşik bash komutları] 
---

# `alias` Komutu

Takma isim atamamızı sağlayan bir komuttur. Bu komut sayesinde dilediğimiz uzunluktaki komutları tek bir takma ad üzerinden çalıştırabiliriz. Hemen basit bir örnek olması için paket yüklememizi sağlayan `sudo apt install` komutuna "**kur**" takma adını atayalım.

``
alias kur="sudo apt install"
``

Bu sayede ne zaman "**kur**" takma adını kullanırsam `sudo apt install` komutu çalışacaktır. Denemek için hem standart hem de yeni atadığımız tak ad ile program kurmayı deneyelim.

```
taylan@taylan:~$ sudo apt install figlet
Paket listeleri okunuyor... Bitti
Bağımlılık ağacı oluşturuluyor       
Durum bilgisi okunuyor... Bitti      
figlet zaten en yeni sürümde (2.2.5-3+b1).
0 paket yükseltilecek, 0 yeni paket kurulacak, 0 paket kaldırılacak ve 2 paket yükseltilmeyecek.
taylan@taylan:~$ kur figlet
Paket listeleri okunuyor... Bitti
Bağımlılık ağacı oluşturuluyor       
Durum bilgisi okunuyor... Bitti      
figlet zaten en yeni sürümde (2.2.5-3+b1).
0 paket yükseltilecek, 0 yeni paket kurulacak, 0 paket kaldırılacak ve 2 paket yükseltilmeyecek.
taylan@taylan:~$
```

Çıktıları kıyasladığımızda takma adın işlevini çok daha net kavrayabiliyoruz. Elbette bizim burada atamış olduğumuz takma adlar yalnızca çalışmakta olduğumu mevcut kabuk için geçerli. Yani bu kabuğu kapattığımızda ya yeni bir alt kabuk açtığımızda bu takma ada ulaşamıyor olacağız. Eğer belirlemiş olduğumuz takma adların oturumumuzda çalıştırılan tüm kabuklarda geçerli olmasını istersek, ev dizinimizde bulunan ***.bashrc*** isimli dosyaya bu takma adları ekleyip kaydetmemiz gerekiyor. Bu sayede biz her oturum açtığımızda bu takma adlar sistem tarafından okunup, oturumumuz altında çalıştırılan tüm alt kabuklar için geçerli olacaktır. Benzer şekilde eğer yalnızca sizin oturumunuzda değil de tüm sistem genelinde(tüm kullanıcı hesaplarında) bu takma adların geçerli olmasını isterseniz de bu takma adları ***/etc/bash.bashrc*** dosyası içerisine ekleyip kaydetmeniz yeterlidir. 

Eğer `alias` komutunu tek başına kullanırsak, mevcut kabuk üzerinde tanımlı olan takma adların listelenmesini sağlayabiliyoruz.

```bash
taylan@taylan:~$ alias
alias kur='sudo apt install'
alias ls='ls --color=auto'
taylan@taylan:~$
```

Benzer şekilde `alias` komutunun `-p` seçeneğini kullandığımızda da takma adların listelenmesini sağlayabiliyoruz.

```bash
taylan@taylan:~$ alias -p
alias kur='sudo apt install'
alias ls='ls --color=auto'
taylan@taylan:~$
```

# `unalias` Komutu

Daha önce atanmış olan takma adları kaldırmak için kullandığımız komuttur. Kaldırmak istediğimiz takma adı `unalias` komutunun ardından belirtmemiz yeterli. Denemek için daha önce tanımlamış olduğum "kur" isimli takma adı `unalias kur` komutu ile kaldırıyorum.

```bash
taylan@taylan:~$ alias -p
alias ara='find'
alias bul='locate'
alias kim='whoami'
alias kur='sudo apt install'
alias ls='ls --color=auto'
taylan@taylan:~$ unalias kur 
taylan@taylan:~$ alias -p
alias ara='find'
alias bul='locate'
alias kim='whoami'
alias ls='ls --color=auto'
taylan@taylan:~$
```

Ayrıca tek seferde tanımlı olan tüm takma adları sıfırlamak istersek `unalias` komutunun `-a` seçeneğini kullanabiliriz.

```bash
taylan@taylan:~$ unalias -a
taylan@taylan:~$ alias -p
taylan@taylan:~$
```