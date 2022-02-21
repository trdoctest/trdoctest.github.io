---
layout: simple
title: Temel Linux Eğitimi
excerpt: "Temel Linux Eğitimi Sıralı Müfredatı"
search_omit: true
---

 
<h1>Sıfırdan Sıralı Temel Linux Eğitimi</h1>
  <p>Temel Linux eğitimi müfredat sıralamasına göre dersler sıralı olarak eklenmiştir. </p>
<div class="row mb-2">
    {% for post in site.egitim | sort: 'title' %}
		<div class="col-md-6">
      <div class="no-gutters border rounded overflow-hidden flex-md-row mb-4 shadow-sm h-md-250 position-relative">
        <div class="col p-4 d-flex flex-column position-static">
 	<h3 class="mb-0">{{ post.title }}</h3>
          <p class="card-text mb-auto">{{ post.excerpt | remove: '\[ ... \]' | remove: '\( ... \)' | markdownify | strip_html | strip_newlines | escape_once }}</p>
          <a href="{{ site.url }}{{ post.url }}" class=" stretched-link"></a>
        </div>
        
      </div>
    </div>
    {% endfor %}
  </div>
