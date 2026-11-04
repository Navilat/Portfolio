---
layout: default
title: Blog & Artículos | Nicolás Ávila
permalink: /blog/
---

# Artículos & Publicaciones

Reflexiones técnicas, arquitectura de software y estrategias prácticas sobre la orquestación y gobernanza de agentes de Inteligencia Artificial en entornos de producción.

---

{% if site.posts.size > 0 %}
  {% for post in site.posts %}
### [{{ post.title }}]({{ post.url | relative_url }})
<small>📅 {{ post.date | date: "%d de %B de %Y" }} • Por **{{ post.author | default: site.title }}**</small>

<p>{{ post.description }}</p>

👉 [Leer artículo completo →]({{ post.url | relative_url }})

---
  {% endfor %}
{% else %}
<p>Próximamente se publicarán nuevos artículos técnicos.</p>
{% endif %}
