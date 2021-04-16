---
layout: simple
title: Harici Kaynaklar
excerpt: "Linux özelinde paylaşımda bulunan,faydalı harici kaynaklar."
search_omit: true
---
<p></p>
<div class="no-gutters border rounded overflow-hidden flex-md-row mb-4 shadow-sm  position-relative">
	  <div class="row no-gutters">
        <div class="col-md-3">
            <a href="{{ site.url }}{{ post.url }}"><img src="{{ site.url }}/assets/img/harici.png" class="card-img-top img1"></a>
        <footer align="center">		
      <small><a href="https://www.freepik.com/">Image Source</a></small>
    </footer>
		</div>
        <div class="col-md-8">
            <div class="card-body">
		<strong class="d-inline-block mb-0 text-primary"><h3 id="alistirma">Harici Kaynaklar</h3></strong>
                <p class="card-text">Linux özelinde paylaşımda bulunan,faydalı harici kaynakların listesi. Yeni kaynak önerileri veya mevcut olanlar hakkında güncelleme iletmek için buradan iletişime geçebilirsiniz. </p>
                
            </div>
			<a href="{{ site.url }}{{ post.url }}" class=" stretched-link"></a>
        </div>
    </div>
	</div> 




<div class="row mb-2">
    {% for post in site.tags.kaynaklar %}
		<div class="col-md-6">
      <div class="no-gutters border rounded overflow-hidden flex-md-row mb-4 shadow-sm h-md-250 position-relative">
        <div class="col p-4 d-flex flex-column position-static">
          
		  <p class="text-primary"><i class="fa fa-calendar" aria-hidden="true"></i> {{ post.modified | date: "%d/%m/%Y" }}</p>		  
          <h3 class="mb-0">{{ post.title }}</h3>
          <p class="card-text mb-auto">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</p>
          <a href="{{ site.url }}{{ post.url }}" class=" stretched-link"></a>
        </div>
        
      </div>
    </div>
    {% endfor %}
  </div>

	