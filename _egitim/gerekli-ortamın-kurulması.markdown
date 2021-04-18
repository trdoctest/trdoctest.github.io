---
layout: tutorial
title:  "2. Ders: Gerekli Ortamın Kurulması"
modified: 2021-04-15
author: Ahmet
excerpt: "Eğitim boyunca gerekli olan çalışma ortamının kurulum alternatiflerini ele alıyoruz."
tags: [usb persistence , live usb , kurulum metodları , sanal linux , vps]
categories: [egitimserisi, temel_linux]
tutorial: [2] 
---
<h1>Gerekli Ortamın Kurulması</h1>
<p>Linux işletim sistemini kurmak veya Linux'u herhangi bir kurulum işlemi gerçekleştirmeden kullanmak için çok fazla seçenek bulunuyor. Ben sadece içlerinde bilmediğiniz bir alternatif seçenek olması ihtimaline karşı <strong>genel kullanım seçeneklerini</strong> aşağıda listeliyorum. </p>
<h2>Kurulum ve Kullanım Metodları</h2>
<ul>
<li>Sanal olarak kurulum (Vmware &amp; Virtualbox)</li>
<li>İkincil işletim sistemi olarak kurmak (Dualboot)</li>
<li>Live versiyon olarak kullanmak.(Tüm dağıtımlarda bu özellik bulunmayabilir.)</li>
<li>Linux VPS aracılığı ile kullanmak.</li>
</ul>
	 
<h3 id="sanal">Sanal Olarak Kullanmak;</h3>
<p><strong>Sanallaştırma işlemi kısaca;</strong> kurmak istediğiniz yeni bir işletim sistemini, diske kalıcı kuruluma ihtiyaç duymadan, mevcut işletim sistemi üzerinden sanallaştırma teknolojisi ile çalıştırabilmeniz anlamına gelir. Sanallaştırma teknolojisi sayesinde, kullanmakta olduğunuz işletim sisteminden çıkmadan, tıpkı program çalıştırır gibi; herhangi bir işletim sistemini sanal olarak çalıştırabilirsiniz.  Sanallaştırma işlemini; bu iş için geliştirilmiş olan <strong>vmware</strong> ve <strong>virtualbox</strong> gibi özel yazılımlar yerine getiriyor.</p>
<div class="alert alert-success">
<h3>Avantajları</h3>
<ul>
<li>Sistemin yedeğini alarak, büyük bir sorun ile karşılaştığımızda
aldığımız yedeği kolaylıkla geri yükleyebiliriz.</li>
<li>Snapshot(anlık görüntü) özelliği sayesinde sistemi olduğu gibi kaydedip, daha sonra istediğimiz zaman kaldığı yerden çalışmaya devam edebiliriz.</li>
<li>Diske kalıcı kurulum gerektirmez, ve kurulu olan sistemin dosyalarına kesinlikle müdahale etmez. Yani kurulu sisteme hiç bir zarar vermeden sanal olarak çalışır.</li>
<li>Aynı anda birden çok işletim sistemini çalıştırabilir.(Bilgisayarınızın performansına göre değişiklik gösterebilir.)</li>
<li>Kendinize göre ayarladığınız sanal makineyi kopyalayıp istediğiniz bilgisayarda aynı şekilde çalıştırabilirsiniz.</li>
</ul>
</div>
<p><strong>Kısacası;</strong> yeni öğrenmeye başlayan kişiler için test alanı görevi görür, snapshot ve yedekleme özellikleri sayesinde hatalardan kolaylıkla geri dönülmesi mümkündür. Eğer; sisteme zarar vermeden gönül rahatlığı ile her şeyi kurcalayayım, deneme yanılma ile öğreneyim derseniz "sanal olarak kullanım" sizin için biçilmiş kaftandır.</p>
<div class="alert alert-danger">
<h4>Dezavantajları</h4>
<p>Sanallaştırmanın sağladığı avantajlarının yanında, dezavantajlarının sayısı ve etkisi çok büyük değildir.</p>
<ul>
<li>Mevcut işletim sistemi üzerinde çalıştığı için performans sorunları yaşanabilir.(Bilgisayarınızın performansına göre değişiklik gösterir.)</li>
<li>Çok fazla yedek alındığında ve çok fazla sanal makine oluşturulduğunda disk alanı ve çalışma organizasyonunuz kötü etkilenebilir.(Sahip olduğunuz organizasyon becerisi ve disk kapasitesi ile bu sorun pek de önemli sayılmaz.)</li>
</ul>
</div>
<p>Söz konusu sanallaştırma olduğunda çeşitli araçlar bulunsa da bizler en sık tercih edilen "Vmware" ve "Virtualbox" araçlarından kısaca bahsedelim.</p>

<p><em><strong>Vmware;</strong></em> ücretli bir yazılımdır ve içerisinde bir çok ekstra özellik barındırır. Bu özellikler genellikle işletmelerin işine yarayacak türdendir. Eğer bireysel bir kullanıcıysanız muhtemelen bir çok ekstra özelliği kullanmanız gerekmez.(Bu fazla özellikler sistemin daha hantal çalışmasına neden olabilir.)</p>
<p><em><strong>Virtualbox:</strong></em> tamamen ücretsiz, vmware ile hemen hemen aynı özelliklere sahip yazılımdır. Üstelik "Windows", "MacOS" ve "Linux" platformlarında kullanılabilir. Eğer bireysel bir kullanıcıysanız; virtualbox yazılımını tercih etmenizi öneririm.(Virtualbox yazılımı içerisinde çok fazla ekstra özellik barındırmadığından bireysel kullanıcılar için vmware yazılımına oranla daha performanslı çalışır.)</p>
	 
<h3 id="ikincil">İkincil İşletim Sistemi Olarak Kullanmak</h3>
<p><strong>Bu yöntem, özetle;</strong> mevcut işletim sisteminin yanına, diskte alan açarak ikincil bir sistem olarak kurmak ve kullanmaktır. Bu kurulumun ardından sistem, başlangıçta hangi işletim sistemini kullanmak istediğinizi sorar ve seçiminize göre ilgili sistemi başlatır.</p>
<div class="alert alert-success">
<h4>Avantajları</h4>
<ul>
<li>Sanal kuruluma oranla performans açısında oldukça verimlidir.</li>
<li>Var olan sistemi silmeden yanına kurduğunuz için, ihtiyacınız olduğunda diğer sisteme geçiş yapabilirsiniz.</li>
</ul>
</div>
<div class="alert alert-danger">
<h4>Dezavantajları</h4>
<ul>
<li>Sistem yedeğini almak ve ilgili yedeğe dönmek, sanal kullanıma oranla daha zahmetlidir.</li>
<li>Snapshot özelliği olmadığından sistemde herhangi bir kritik hata meydana geldiğinde, sistemi onarması çok daha uzun sürebilir.</li>
<li>Kurulum işlemi ve kurulum sonrası sistem ayarlarının yapılandırılması, diğer kurulum işlemlerine oranla biraz daha uğraştırıcı olabilir.</li>
</ul>
</div>
<p>Öğrenme aşamasında, kullanıcıların hata yapması çok doğal bir durumdur. Etkili öğrenim için sizlerin de bildiği üzere uygulama yaparak ilerlenmesi şarttır. Uygulamalar esnasında kullanıcılar sürekli deneme yanılma yöntemiyle yeni şeyler keşfeder ve daha fazlası için sistemi kurcalar. Sistemin kullanımı sırasında meydana gelebilecek olası hatalar, yeni başlayan kullanıcıların öğrenme şevkini kırarak öğrenme sürecini sekteye uğratabilir. Eğer Linux işletim sistemini ilk defa kullanacaksınız, daha hızlı ve etkili öğrenebilmek için bu yöntemi(İkincil İşletim Sistemi) kullanmayın. Ancak sanal olarak kullandığınızda sistem performansı sizin için çok sorun oluyorsa elbette bu yöntem ile de eğitime devam edebilirsiniz. Yine de yeni başlayan kullanıcıların bu kullanım yönteminden önce diğer kullanım alternatiflerini de değerlendirmesi faydalı olacaktır. <strong>Bu yüzden lütfen yazının tamamını okuyup sizin için en ideal olan yönteme kendiniz karar verin.</strong></p>
	 
<h3 id="live">Live Versiyon Olarak Kullanmak</h3>
<p>Live olarak kullanmak; Linux işletim sistemini USB diskimiz üzerine kurup, sistemi bu USB disk ile başlatıp Linux işletim sistemini bu USB disk üzerinden kullanmaktır. Üstelik USB üzerinden kullanımda tek bir kullanım modu da bulunmuyor. Aşağıda farklı kullanım modları sırasıyla açıklanmıştır. <strong>"Live Versiyon Olarak Kullanma" seçeneğini, sanal kullanımda performans sorunu yaşayan arkadaşlara kesinlikle öneririm.</strong> Ancak maalesef ki tüm dağıtımlar live kullanımı doğrudan desteklemiyor. Doğrudan live modu desteklenmediğinde uygulanabilecek çözümler olsa da bu konu temel eğitimin dışındadır. İleride bir blog yazısı ile ayrıca bu konuya değinebiliriz. Yine de Kali Linux gibi live modunu destekleyen bir dağıtım kullanıyorsanız bu modu da mutlaka deneyimlemenizi öneririm. </p>
<div class="alert alert-success">
<h5>Avantajları</h5>
<ul>
<li>Sabit diske kurulum gerektirmez, yalnızca USB disk yeterlidir.</li>
<li>Bir çok ihtiyaca göre bir çok kullanım modu vardır.</li>
<li>Live modu sayesinde sistemi kurcalamaktan korkmadan etkili öğrenme sağlayabilirsiniz.</li>
</ul>
</div>
<div class="alert alert-danger">
<h5>Dezavantajları</h5>
<ul>
<li>Bu kullanımdan verim alabilmek için en az <strong>8 GB</strong> USB diskiniz olmalı.</li>
<li>Boot etmek için bir kaç ön hazırlık gerekir.</li>
</ul>
</div>	
<h4> Boot Menüsünde Yer Alan Seçenekler</h4>
<p>Daha önce de belirttiğimiz şekilde, tüm dağıtımlarda USB üzerinden kullanım seçenekleri bire bir aynı değildir. Yine de ben anlatım sırasında Kali Linux kullanacağım için, Kali Linux dağıtımının USB üzerinden kullanımını desteklediği modlara kısaca değinmek istiyorum.</p>
<p><img src="{{ site.url}}/egitimserisi/img/0-%20Gerekli%20Ortam%C4%B1n%20Kurulmas%C4%B1/boot-menu.jpg" class="responsive"></p>
<h4>Live:</h4>
<p>Kali Linux işletim sistemini USB diskiniz üzerinden kullanırsınız ve <strong>sistemi kapattığınızda</strong>  veya USB diskinizi bilgisayardan çıkardığınızda  <strong>sistemde yaptığınız tüm değişiklikler silinir.</strong>  Yani bu mod isminden de anlaşılacağı gibi yalnızca kullanım sırasında bilgileri tutar, daha sonra sistem kapandığında tüm bilgiler silinir ve sistem ilk baştaki haline döner. Bu mod sayesinde her defasında üzerinde hiç bir değişiklik yapılmamış temiz bir sistem üzerinde çalışabilirsiniz.</p>
<h4>Live (failsafe):</h4>
<p>Tıpkı live modunda olduğu gibi bilgileri yalnızca kullanım sırasında tutar. Genellikle sistemde sorun meydana geldiğinde sorunun kaynağını anlamak adına kullanılan, <strong>güvenli mod</strong>  diye tabir edilen moddur.</p>
<h4>Live (forensic mode):</h4>
<p>Adli moddur, ve mevcut sistem üzerinde inceleme yapılacağı zaman tercih edilir. Bu mod  <strong>mevcut sistemde hiç bir kalıntıya ya da değişikliğe neden olmadan sistemin incelenebilmesine</strong> olanak tanır. Genellikle bir suçun kanıtlanması gibi olaylarda tercih edildiği için adli(<strong>forensic</strong>) mod olarak tabir edilir.</p>
<h4>Live USB Persistence:</h4>
<p>Kali Linux işletim sistemini USB diskiniz üzerinden tıpkı sabit bir diske kurulmuşcasına kullanabilmenize olanak sağlar. Bu mod ile sistemde yapılan tüm değişiklikler USB disk üzerinde kayıt olur ve daha sonra bu bilgilere tekrar bu mod aracılığı ile ulaşabilirsiniz. Yani  <strong>live modunun kalıcı halidir. Sistemde yapılan tüm değişiklikler tekrar ulaşabileceğiniz şekilde kalıcı olarak USB üzerine yazılır.</strong></p>
<h4>Live USB Encrypted Persistence:</h4>
<p>Bu mod ise bir üst kısımda bahsedilen kalıcı(persistence) modun şifrelenmiş halidir. Diğer moddan farklı olarak "Encrypted" isminden de anlaşılacağı üzere, <strong>sistemde yapılan değişiklikler diske yazılırken şifrelenerek kayıt edilir.</strong> Diskin şifresi bilinmeden kalıcı bilgilere ulaşmak ya da disk şifresini sıfırlamak mümkün değildir. USB diskin kolayca kaybolup istenmeyen kişilerin eline geçme ihtimali için bu modun kullanımı tavsiye edilir. Yine de şifrenin unutulmaması kalıcı bilgilere ulaşma noktasında oldukça kritiktir.</p>
<h4>Install:</h4>
<p>Sabit diske kurulum işlemini başlatmak için kullanılan seçenektir.</p>
<h4>Graphical Install:</h4>
<p>Sabit diske kurulum işlemini  <strong>grafiksel arayüz</strong> ile başlatmak için kullanılan seçenektir.</p>
	 
<h3 id="vps">VPS Üzerinden Kullanım</h3>
<p>Uzaktaki özel bir sunucu sistemine bağlanılarak, bağlanılan sistemi herhangi bir yüksek donanım gücüne ihtiyaç duymadan yönetebilmemize olarak tanır.  Özetle; sizin istediğiniz işletim sistemini uzak sunucuda başlatılır, siz de bu sistemi uzaktan komutlar vererek yönetirsiniz.</p>
<div class="alert alert-success">
<h4>Avantajları</h4>
<ul>
<li>Mevcut donanımınızın çok güçlü olması gerekmez.</li>
<li>İstenilen yerden ve istenilen cihazdan(<em>pc, laptop, tablet, telefon..</em>) uzak sunucudaki sisteme komut verilebilir.</li>
<li>Sistem yedeği alma ve üst düzey sistem performansı imkanı vardır.</li>
</ul>
</div>
<div class="alert alert-danger">
<h4>Dezavantajları</h4>
<ul>
<li>Bu hizmetler ücretlidir.</li>
</ul>
</div>
<p>Bu kısımda neden kurulum detaylarını anlatmıyorsun diyecek olursanız, burada izahı dokümantasyonu uzatacak ve çok da verimli olmayacaktır. Kurulum işlemini verimli şekilde anlatabilmek için en iyi yol, kurulum işlemlerini videolu şekilde göstermektir. Dilerseniz bu dokümantasyonun <a target="_blank" href="https://www.udemy.com/course/kali-linux-ile-sifirdan-temel-linux-egitimi/?referralCode=04ABD09E6ED5DA93F7A2" rel="nofollow">video eğitiminden</a> ya da internette araştırma yaparak kurulum işlemleri hakkında detaylıca bilgi edinebilirsiniz.</p>
