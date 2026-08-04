---
tipo: referencia
citekey: {{citekey}}
autores: {{authors}}
año: {{date | format("YYYY")}}
revista: {{publicationTitle}}
doi: {{DOI}}
estudiante: 
verificada: false
estado_lectura: en_proceso
tags: [referencia]
---

# {{title}}

- **Cita APA 7:** {{bibliography}}
- **DOI verificado en:** (Crossref / OpenAlex / editorial) — fecha
- **Para qué tesis sirve:** [[]]

## Abstract
> {{abstractNote}}

## Notas de lectura (3 niveles: externo vs interno)

{% for color, annots in annotations | groupby("color") -%}

{% if color == "#ffd400" %}### 🟡 Ideas principales
{% elif color == "#ff6666" %}### 🔴 Contradicciones / tensiones
{% elif color == "#5fb236" %}### 🟢 Confirmaciones / respaldo
{% elif color == "#2ea8e5" %}### 🔵 Definiciones / conceptos
{% elif color == "#a28ae5" %}### 🟣 Metodología
{% elif color == "#f19837" %}### 🟠 Citas textuales para usar
{% else %}### Otros resaltados
{% endif %}

{% for annotation in annots -%}
> "{{annotation.annotatedText}}" (p. {{annotation.page}})
{% if annotation.comment %}
**Mi nota:** {{annotation.comment}}
{% endif %}

{% endfor %}
{% endfor %}

## Notas de lectura derivadas
- [[]]
