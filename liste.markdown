---
layout: page
title: Konu Etiketleri
excerpt: "Tüm içeriklerin kategorize etiket listesi."
search_omit: true
---


  {% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
{% assign tags_list = site_tags | split:',' | sort %}

<div align="center"><h1>Etiket Listesi</h1><p> Etiketlerine göre kategörize şekilde gruplanmış listedir.</p></div>
<h2>Mevcut Etiketlerin Özeti</h2>

<ul class="card-columns">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
    <li><a href="#{{ this_word }}">{{ this_word }}: <span class="badge badge-primary badge-pill">{{ site.tags[this_word].size }}</span></a></li>
  {% endunless %}{% endfor %}
</ul>


{% for item in (0..site.tags.size) %}{% unless forloop.last %}
  {% capture this_word %}{{ tags_list[item] | strip_newlines }}{% endcapture %}
  <div class=" border rounded mb-4 shadow-sm col">
  <h2 id="{{ this_word }}">{{ this_word }}</h2>
  
  <ul class="post-list card-columns">
  {% for post in site.tags[this_word] %}{% if post.title != null %}
    <li><a href="{{ site.url }}{{ post.url }}">{{ post.title }} </a></li>
  {% endif %}{% endfor %}
  </ul>
</div>
{% endunless %}{% endfor %}

  {% assign post = page %}
{% if post.tags.size > 0 %}
    {% capture tags_content %}Posted with {% if post.tags.size == 1 %}<i class="fa fa-tag"></i>{% else %}<i class="fa fa-tags"></i>{% endif %}: {% endcapture %}
    {% for post_tag in post.tags %}
        {% for data_tag in site.data.tags %}
            {% if data_tag.slug == post_tag %}
                {% assign tag = data_tag %}
            {% endif %}
        {% endfor %}
        {% if tag %}
            {% capture tags_content_temp %}{{ tags_content }}<a href="/blog/tag/{{ tag.slug }}/">{{ tag.name }}</a>{% if forloop.last == false %}, {% endif %}{% endcapture %}
            {% assign tags_content = tags_content_temp %}
        {% endif %}
    {% endfor %}
{% else %}
    {% assign tags_content = '' %}
{% endif %}
