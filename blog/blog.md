---
layout: simple
title: Blog İçerikleri
excerpt: "Blog üzerinde paylaşılan tüm içeriklerin listesi."
search_omit: true
---
<h1>Tüm Blog İçeriği</h1>
  <p>Düzenlenme tarihine göre yeniden eskiye doğru, paylaşılmış olan tüm içeriklerin listesidir. </p>

<div class="row mb-2">
    {% for post in site.posts%}
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