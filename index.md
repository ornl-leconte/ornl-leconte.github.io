---
layout: page
header-img: img/logo/svg-notext.svg
---

{% for post in site.posts %}
<div class="post-preview">
    <a href="{{ post.url | prepend: site.baseurl }}">
        <h2 class="post-title"> {{ post.title }}
        </h2>
        {% if post.subtitle %}
        <h3 class="post-subtitle">
            {{ post.subtitle }}
        </h3>
        {% endif %}
    </a>

    <!--  on {{ post.date | date: "%B %-d, %Y" }} -->
    <p class="post-meta">Posted by {% if post.author %}{{ post.author }}{% else %}{{ site.title }}{% endif %}</p>

</div>
<hr>
{% endfor %}
