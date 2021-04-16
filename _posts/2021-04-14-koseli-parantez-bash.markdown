---
layout: post
title:  "[ ] (Köşeli Parantez) Komutu"
modified: 2021-04-14
excerpt: "Bash kabuğunda yerleşik olarak bulunan köşeli parantezin kullanım açıklamasıdır."
tags: bash bash_builtin bash_yerleşik_komutlar 
tags: [bash, bash builtin, yerleşik bash komutları] 
---

Köşeli parantezler test komutu ile aynı görevi yerine getirebilir yani `test` komutu yerine kullanılabilir. Köşeli parantezler, içerisinde yer alan koşul durumunu test edip çıkış kodu olarak **0** veya **1** değerlerini döndürür. Yani köşeli parantezlerin kullanım amacı, içerisinde belirtilmiş olan koşulun sağlanıp sağlanmadığını test etmektir. Tek başına aşağıdaki şekilde kullanılabileceği gibi elbette koşullara bağlı çalışan yapılar kurarken `if/else` koşulu içerisinde de kullanılabilir. 

Örneğin ben ev dizinimde "***.bashrc***" isimli dosyanın olup olmadığını test etmek için aşağıdaki yapıyı kullanabilirim. Test sonucu almak için de **`echo $?`** komutu ile çıkış değerini kontrol edebilirim. Eğer çıkış kodu "**0**" ise dosya vardır "**1**" ise dosya yoktur. 

**Not:** Çıkış kodlarının durumu ikili sayısı sistemi ile karıştırılmamalıdır. Burada bahsi geçen çıkış kodları bash kabuğunda tanımlı olan çıkış kodlarıdır. Bir komut hatasız çalışırsa "**0**" değeri döndürülürken eğer komut hata verirse "**1**" değeri döndürülür. Bu konu hakkında daha fazla detay öğrenmek için çıkış kodlarını açıkladığımız kısıma göz atabilirsiniz.

```bash
$ [ -f ~/.bashrc ]
$ echo $?
0         # Çıktı "0" yani "hatasız" çıkış kodu olduğu için dosya var.
```

Şimdi de olmayan bir dosya ismi yazıp aynı testi devam ettirelim.

```bash
$ [ -f ~/.olmayan-dosya]
$ echo $?
1         # Çıktı "1" yani "hatalı" çıkış kodu olduğu için dosya yok.
```

Eğer daha önce `if/else` ile koşul tanımlaması yaptıysanız zaten köşeli parantez kullanmışsınızdır. İşte burada kullanılan köşeli parantez de aslında belirtilmiş olan koşulun çıkış kodunu "**0**" ya da "**1**" şeklinde `if` yapısına iletiyor. `if` bloğu; eğer aldığı çıkış kodu "**0**" yani "**koşul sağlanıyor**" şeklindeyse `if` durumu için belirtilmiş olan komutları çalıştırıyor. Aksi halde çıkış kodu "**1**" yani "**koşul sağlanmadı**" şeklindeyse bu kez else bloğuna geçilip bu blok altında belirtilmiş olan komutlar çalıştırılıyor. Bu süreç kurulan koşul yapısına göre bu şekilde devam eder.

```bash
if [ durum-koşullar ] #Bir koşul belirtir.
then #Koşul sağlanırsa yapılacaklar.
	echo "ilk koşul sağlandı !"
else #Hiç bir koşul sağlanmaz ise yapılacaklar..
	echo "ilk koşul sağlanmadığı için bu komut çalıştırıldı"
fi
```

Burada köşeli parantez yalnızca koşul durumlarını test ediyor. Koşulları test ederken parantez açılışında ve kapanışında birer boşluk olması gerekiyor. Aksi halde karşılaştırma yapılamaz.

# [[ ]] Çift Köşeli Parantez Kullanımı

Aslında bu kullanım da tıpkı tek köşeli parantez kullanımı gibidir fakat aralarındaki en temel farklılık; tek köşeli parantez yerleşik komut(builtin) iken, çift köşeli parantez anahtar kelimedir(keyword).

**Anahtar kelimeler;** kabuk tarafından belirli görevleri yerine getirmeleri için özel olarak ayrılmış olan kelimelere verilen genel isimdir. Anahtar kelimeler aslında kabuğun sözdiziminin yapı taşlarıdır. Anahtar kelimeler kabuğun daha kolay programlanabilmesini sağlar. İngilizce olarak "**keyword**" olarak isimlendirilmiştir. Anahtar kelimeler aslında tek başına kullanıldıklarında genelde işlevsizdirler. İşlevsel olmaları için araçlara yani yerleşik olan ya da olmayan herhangi bir aracın çalıştırılmasına ihtiyaçları vardır. Bash kabuğunda ayrılmış olan anahtar kelimeleri görmek için `compgen -k` komutunu kullanabiliriz.

Çift köşeli parantez aslında bash kabuğunun test ya da tek köşeli parantezden ziyade daha işlevsel şekilde koşul durumlarını test etmek için kullandığı yapıdır. Çift köşeli parantez içerisine yazılmış olan tüm ifadeler koşul durumunu test etme kapsamında ele alınır. Bu ne demek oluyor ? Tek köşeli parantez aslında bir komut olduğu için komuttan sonra girilen tüm argümanlar bash tarafından ayrıştırılıp çoklu işlevleri arasından anlamlandırılmaya çalışılır. Bu da bizim ifade etmek istediğimiz anlam dışında farklı mantık hatalarına sebep olabilir.

Tek köşeli parantez yerine çift köşeli parantez kullanmak, komut dosyalarındaki birçok mantık hatasını önleyebilir. Çünkü çift köşeli parantez içerisindeki her şeyin koşul belirtmek üzere yazıldığı kabuk tarafından bilinir. Örneğin, `&&`, `||`, `<` ve `>` operatörleri, tek köşeli parantez yapısında hata vermelerine rağmen çift köşeli parantez içerisinde doğru şekilde çalışırlar. Bu durumu aşağıdaki basit örneğimiz üzerinden teyit edelim.

Örnek olması için `a=5 b=10` şeklinde iki değişken tanımlayalım ve bu değişkenlerin ürettikleri çıkış kodlarına bakalım.

```bash
taylan@taylan:~$ a=5
taylan@taylan:~$ b=10
taylan@taylan:~$ [ a < b ] # a değişkeni b değişkeninden küçük müdür ?
bash: b: Böyle bir dosya ya da dizin yok
```

Gördüğünüz gibi tek köşeli parantez kullanarak `a` değişkeninin `b` değişkeninden küçük olup olmadığını sorguladığımızda, küçüktür işareti(`<`) bash tarafından kıyaslama anlamı dışında yönlendirme anlamında ele alındığı için hata verdi. Bu durumdan kaçınmak için özellikle bu işaretin küçüktür anlamına geldiğini kaçış karakteri olan tersh slash `\` işareti ile belirtmemiz gerekiyor.

```bash
taylan@taylan:~$ [ a \< b ] # a değişkeni b değişkeninden küçük müdür ?
taylan@taylan:~$ echo $?
0    # Çıkış kodu "0" yani a değişkeni b den küçüktür.
```

Şimdi aynı örneğimizi çift köşeli parantez ile deneyelim.

```bash
taylan@taylan:~$ a=5
taylan@taylan:~$ b=10
taylan@taylan:~$ [[ a < b ]] # a değişkeni b değişkeninden küçük müdür ?
taylan@taylan:~$ echo $?
0
```

Gördüğünüz gibi çift köşeli parantez içerisinde belirtmiş olduğumuz küçüktür (`<`) işareti tam da bizim kast ettiğimiz şekilde yani koşul kıyaslama anlamında ele alındı. Çift köşeli parantez kullanımı olası mantık hatalarının önüne geçtiği için koşul durumları için öncelikli olarak kullanılması tavsiye edilir. Fakat posix standartlarında yer almadığı için taşınabilir bir betik programlıyorsanız tek köşeli parantez kullanmanız çok daha doğru olacaktır. Tek köşeli parantez posix standartları dahilinde olan kabuklarda geçerli olacağı için farklı ortamlarda çalıştırılabilme kabiliyeti yani taşınır olma özelliği daha fazladır.