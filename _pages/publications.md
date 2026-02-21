---
title: "Publications & Preprints"
permalink: /publications/
layout: archive
---

{%- assign pubs = site.publications | sort: "date" | reverse -%}
{%- assign N = pubs | size -%}

<ol>
  {%- for p in pubs -%}
  {%- assign k = N | minus: forloop.index0 -%}
  {%- capture author_part -%}{% if p.authors %} ({{ p.authors }}){% endif %}{%- endcapture -%}
  {%- assign author_part = author_part | strip -%}

  <li value="{{ k }}">
   {{ p.title }}{% if author_part != "" %} {{ author_part }}{% endif %}.
   {% if p.venue %} <em>{{ p.venue }}</em>{%- endif -%}
   {%- if p.volume -%}, {{ p.volume }}{%- endif -%}
   {% if p.year %} ({{ p.year }}){%- endif -%}
   {%- if p.number -%}, no. {{ p.number }}{%- endif -%}
   {%- if p.pages -%}, {{ p.pages }}{%- endif -%}.
   {%- if p.doi_url or p.pdf_url or p.arxiv_url -%}
   <br>
   <span class="page__meta">
     {%- if p.doi_url -%}<a href="{{ p.doi_url }}">DOI</a>{%- endif -%}
     {%- if p.pdf_url -%}{%- if p.doi_url -%}&nbsp;|&nbsp;{%- endif -%}<a href="{{ p.pdf_url }}">PDF</a>{%- endif -%}
     {%- if p.arxiv_url -%}{%- if p.doi_url or p.pdf_url -%}&nbsp;|&nbsp;{%- endif -%}<a href="{{ p.arxiv_url }}">arXiv</a>{%- endif -%}
   </span>
   {%- endif -%}
  </li>
  {%- endfor -%}
</ol>
