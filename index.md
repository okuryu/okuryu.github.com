---
layout: default
title: Ryuichi Okumura
---
<p><img src="http://farm5.static.flickr.com/4014/4586084325_f5ef8fc065_z.jpg" width="640" height="420"></p>

Web and Photography.

### Recent Posts

<ul class="posts">
{% for post in site.posts limit:10 %}
<li><a href="{{ post.url }}">{{ post.title }}</a></li>
{% endfor %}
</ul>

<p class="archives"><a href="/archives.html">view all posts</a></p>
