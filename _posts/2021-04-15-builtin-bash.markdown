---
layout: post
title:  "builtin Komutu"
modified: 2021-04-15
author: taylan_ozgur_bildik
excerpt: "Bash kabuğunda yerleşik olarak bulunan builtin komutunun kullanım açıklamasıdır."
tags: [bash, bash builtin, yerleşik bash komutları]
categories: blog 
---

Builtin kelimesi Türkçe olarak "yerleşik-dahili" anlamına geliyor ve bash kabuğu içerisinde halihazırda kullanılabilir olan araçları temsil etmek için kullanılıyor. Bash kabuğu üzerinde yerleşik olan komutları görmek için konsola `compgen -b` komutunu girebiliriz. 

```bash
taylan@taylan:~$ compgen -b
. : [ alias bg bind break builtin caller cd command compgen complete compopt continue declare dirs disown echo enable eval exec exit export false fc fg getopts hash help history jobs kill let local logout mapfile popd printf pushd pwd read readarray readonly return set shift shopt source suspend test times trap true type typeset ulimit umask unalias unset wait
```

Girmiş olduğumuz komut neticesinde içerisinde `builtin` komutunun da dahil olduğu bash kabuğunda yerleşik olan komutların listesini almış olduk.

Burada bahsi geçen `builtin` komutunun işlevi; eğer kullanıcı tarafından bash kabuğunun yerleşik komutları ile aynı isme sahip olan fonksiyon tanımlandıysa, tanımlanmış olan yeni fonksiyon yerine öncelikli olarak yerleşik komutu çalıştırıyor. Aslında `builtin` komutu genellikle bash programlama yaparken kullanılır. Çünkü yerleşik olan komutlar `builtin` komutu ile özellikle belirtildiğinde, betik dosyasının çalıştırıldığı sistem yerleşik komutların isimlerini yeni fonksiyon tanımlarken kullanmışsa yani özelleştirme yapmış olsa dahi yalnızca bash kabuğunun sahip olduğu yerleşik komutlar çalışır. Bu da betik dosyasının daha taşınabilir olmasına yani özelleştirilmiş sistemlerde bile sorunsuzca çalışmasına yardımcı olur.

Hemen denemek için `cd` komutu ile aynı isimde bir fonksiyon tanımlayalım. Bu fonksiyonun görevi de komut satırına çıktı bastırmak olsun. Fonksiyon tanımlama işleminin ardından `cd` komutunun asıl işlevi olan dizin değiştirme işlemini de test edelim. 

```bash
taylan@taylan:~$ function cd {
> echo "cd komutunu ekarte eden fonksiyonum ben :)"
> }
taylan@taylan:~$ cd Masaüstü
cd komutunu ekarte eden fonksiyonum ben :)
```

Görebildiğiniz gibi `cd` komutu ile aynı isimde yeni bir fonksiyon tanımladığımızda bu fonksiyon `cd` komutunun işlevini geçersiz kılıyor. Bu durumun önüne geçmek için `builtin` komutu ile bizim "**cd**" ifadesini kullanarak aslında bash yerleşik komutunu kullanmak istediğimizi özellikle belirtmemiz gerekiyor.

```bash
taylan@taylan:~$ builtin cd Masaüstü
taylan@taylan:~/Masaüstü$ pwd
/home/taylan/Masaüstü
taylan@taylan:~/Masaüstü$ cd 
cd komutunu ekarte eden fonksiyonum ben :)
taylan@taylan:~/Masaüstü$
```

Neticede `builtin` komutunun olmadığı kısımlarda "**cd**" ifadesi kabuk tarafından fonksiyon olarak algılanıyor.