---
layout: page
title: "Archive"
description: This page displays all posts.
---


<!-- 
    ---
    layout: page
    title: "Archive"
    description: This page displays all posts.
    header: All Post
    --- 
-->

### Archive of All Post: 

<ul>
    {% for post in site.posts %}

        <li>
            <a href="{{ post.url | prepend: site.baseurl }}">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }} [ {{ post.author }} ] </a>
        </li>


    {% endfor %}
</ul>



***


### Posts by Author : Ikhwan 

<ul>
{% for post in site.posts %}
    {% if post.author contains "Ikhwan" %}
        <li>
            <a href="{{ site.url }}{{ site.baseurl }}{{ post.url}}.html" target="_blank">{{ post.date | date: "%-d %B %Y" }} - {{ post.title }} [ {{ post.author }} ] </a> 
        </li>
    {% endif %}
{% endfor %}
</ul>


***
By: Ikhwan@fedora41.linux