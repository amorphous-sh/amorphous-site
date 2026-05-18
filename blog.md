---
layout: default
title: Blog
permalink: /blog/
---

## Blog

<table>
  <thead>
    <tr>
      <th>Date</th>
      <th>Title</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    {% for post in site.posts %}
    <tr>
      <td><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%Y-%m-%d" }}</time></td>
      <td><a href="{{ post.url | relative_url }}">{{ post.title }}</a></td>
      <td>{{ post.description | default: post.excerpt | strip_html | truncate: 80 }}</td>
    </tr>
    {% endfor %}
  </tbody>
</table>
