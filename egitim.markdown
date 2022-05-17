---
layout: simple
title: Temel Linux Eğitimi
excerpt: "Temel Linux Eğitimi Sıralı Müfredatı"
search_omit: true
---

 
<h1 align="center">Eğitim Serileri</h1>
<p> Buradaki eğitimler, birbirinden bağımsız olarak oluşturulmuştur. İhtiyacınıza yönelik eğitimi seçip, sıfırdan sıralı şekilde takip edebilirsiniz. Eğitimler benzeri konuları farklı kapsamlarda ele aldığı için bazı ortak dersler ve konu tekrarları ile karşılabilirsiniz. Ortak bazı konular olmasına karşın eğitim serilerini farklı ihtiyaçları karşılabilmek adına birbirinden bağımsız olarak ele alındığını dikkate alarak ilerleyin lütfen.</p>

<h2>Herkes için Temel Linux Eğitimi</h2>
  <p>Linux'u kişisel veya farklı disiplenlerdeki gereksinimler dolayısıyla temel düzeyde öğrenmek istiyorsanız buradaki eğitim serisini takip edebilirsiniz. Bu eğitim profesyonel anlamda sistem yöneticiliğinden ziyade herkese genel Linux kullanımı hakkında bilgi sunmak için hazırlanmıştır.</p>
<div class="row mb-2">
    {% for post in site.egitim | sort: 'title' %}
		<div class="col-md-6">
      <div class="no-gutters border rounded overflow-hidden flex-md-row mb-4 shadow-sm h-md-250 position-relative">
        <div class="col p-4 d-flex flex-column position-static">
 	<p class="text-primary">{{ post.tutorial }}. Doküman</p>
          <h3 class="mb-0">{{ post.title }}</h3>
          <p class="card-text mb-auto">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</p>
          <a href="{{ site.url }}{{ post.url }}" class=" stretched-link"></a>
        </div>
        
      </div>
    </div>
    {% endfor %}
  </div>
  
<h2>Linux Sistem Yöneticiliğine Giriş Eğitimi</h2>
<p>Profesyonel anlamda Linux sistem yöneticiliğine giriş için bu eğitim iyi bir başlangıç olabilir. Doğrudan herhangi bir sertifika programı kapsamında hazırlanmış olmasada, GCUX - GIAC Linux+ CompTIA LPI LFCS Oracle Linux RHCE gibi sertifika sınavlarına hazırlanırken kısmi olarak yararlanabileceğiniz bir kaynak olarak kullanabilirsiniz. Eğitim müfredatı şahsi kanaatime göre temelde bilinmesi gereken konuların kapsamı dahilinde hazırlandığı için size herhangi bir sertifika veya nihai sonuç için garanti veremem. Ancak yine de en azından Türkçe kaynak olarak Linux için bir başlangıç noktası olarak görülebilir. </p>
{% include temel-linux-egitimi-card.html %}

<h2>Linux Sistem Yöneticiliği Orta Seviye Eğitim <span class="badge badge-warning "> Yayınlanmadı! </span></h2>
<p>Giriş seviyesi için uygun olmadığını düşündüğüm diğer konuları bu eğitim altında toplamak istedim. Eğitime 2. seviye ya da orta seviye dedim ancak seviyenin tanımı ve kapsamı oldukça muğlak. Yani buradaki eğitim Linux üzerindeki tüm orta seviye konuları kapsamıyor. Sistem yönetimi için temelde ihtiyaç duyabileceğimiz ama bana göre orta seviye dahilinde olan konular kapsamında anlatım gerçekleştiriyor olacağız. İlk eğitimde olduğu gibi bu eğitim de herhangi bir sertifikasyon sınavına hedeflemiyor, yalnızca daha fazlasını araştırmanıza ön ayak olacak kadar bazı konulardan bahsediyor olacağız.</p> 
<div class="alert alert-warning"><strong>Not:</strong> Henüz bu eğitimi hazırlamak için gereken vakte ve motivasyona sahip değilim. Yine de kendimi hazırlamaya mecbur etmek için buraya da eklemek istedim. Bu listede olması kesin hazırlacağım anlamına gelmiyor. 🤷</div>

{% include temel-linux-egitimi-card.html %}

<h2>Bash Kabuk Programlama Eğitimi</h2>
<p>Bash kabuğunu daha yakından tanıyıp hem interaktif kullanımı hem de programlanabilmesi için ele aldığımız derslerdir. Bu eğitim bash kabuğu hakkında tüm bilgiyi içerdiğini iddia etmese de Türkçe için temel düzey bilgi sunma amacındadır.</p>
{% include temel-bash-egitimi-card.html %}
<div class="list-group">
    <a href="#" class="list-group-item list-group-item-action active">
    Sıkça Sorulan Sorular
   </a>
	<a class="list-group-item list-group-item-action" data-toggle="collapse" href="#collapse16" role="button" aria-expanded="false" aria-controls="collapse16">
        <i class="fa fa-angle-down"></i> Eğitime katılmak için gereksinimler neler ?
    </a>
	<div class="collapse" id="collapse16">
  <div class="card card-body">
   <li>Eğitim tamamen ücretsiz ancak eğitimi uygulama yaparak tamamlamak için disiplinli çalışmanız gerekiyor.</li>
   <li>Fiziksel gereklilik olarak Bash kabuğunu kullanabileceği ortam için bir bilgisayar ve mümkünse dokümanın takibi için internete sahip olmanız gerek. Eğer sürekli İnternet bağlantınız yoksa buradaki rehberi takip ederek dokümanın en güncel halini pdf olarak kaydedebilirsiniz.</li>
	  </div>
  </div>
	<a class="list-group-item list-group-item-action" data-toggle="collapse" href="#collapse15" role="button" aria-expanded="false" aria-controls="collapse15">
        <i class="fa fa-angle-down"></i> Bu eğitim kimler için ? 
    </a>
	<div class="collapse" id="collapse15">
  <div class="card card-body">
  <li>Bash kabuğunu aktif olarak kullanması gereken, siber güvenlik sistem yöneticiliği ve kabuk kullanımı ile kesişimi olan herkes için uygun bir eğitimdir.</li>
   <li>Gündelik kullanımda sık tekrar edilen işlerini bash kabuğu ile otomatize hale getirmek isteyenler</li>
   <li>Sistem yöneticiliği anlanında kullanmak isteyenler.</li>
   <li>Bash kabuğunu öğrenerek, programlama kabiliyetinin yanında etkileşimli kabuk kullanımında verimliğini arttırmak isteyenler.</li>
	  </div>
  </div>
		  <a class="list-group-item list-group-item-action" data-toggle="collapse" href="#collapse14" role="button" aria-expanded="false" aria-controls="collapse14">
        <i class="fa fa-angle-down"></i> Eğitim sonunda neler öğrenmiş olacağız ?
    </a>
	<div class="collapse" id="collapse14">
  <div class="card card-body">
  <li>Alternatif kabuklardan ziyade neden bash kabuğunu tercih ettiğimizi ve bash kabuğunun kısa tarihçesini</li>
   <li>Bash kabuğuna girdiğimiz komutların kabuk tarafından nasıl anlaşıldığını.</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
   <li>Değişkenlerin kullanımını</li>
	  </div>
  </div>
	  
    

</div>
