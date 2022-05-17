---
layout: simple
title: Konu Etiketleri
excerpt: "Tüm içeriklerin kategorize etiket listesi."
search_omit: true
---


  {% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}

<div align="center"><h1>Etiket Listesi</h1><p> Etiketlerine göre kategörize şekilde gruplanmış listedir.</p></div>

<ul class="card-columns">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
    <li><a href="#{{ this_word }}">{{ this_word }}: <span class="badge badge-primary badge-pill">{{ site.tags[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>
<hr>
<div class="alert alert-primary"><strong>ℹ️ Not:</strong> Birden fazla etikete sahip olan konuları farklı etiket başlıkları altında tekrar tekrar görebilirsiniz.</div>

{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  <div class=" border rounded mb-4 shadow-sm col p-4">
  <h2 id="{{ this_word }}">{{ this_word }}</h2>
  <hr>
  <ul>
  {% for post in site.tags[this_word] %}{% if post.title != null %}
    <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} </a></li>
  {% endif %}{% endfor %}
  </ul>
</div>
{% endunless %}{% endfor %}

  
