---
tipo: recurso
tags: [sistema, zotero, referencias]
---

# Integración Zotero-Obsidian para el SATG

> Adaptado del flujo `obsidian-tesis-flujo` (repo propio). Diferencia clave: allá gestiona UNA tesis propia; aquí gestiona una **cartera de tesis de asesorados** — por eso se organiza por estudiante, no por subtema.

## Requisitos (una sola vez)
1. **Zotero** + plugin **Better BibTeX** (citekeys estables).
2. Obsidian: plugins **Zotero Integration**, **Dataview**, **Templater**.
3. Export automático `.bib` de la biblioteca (Better BibTeX → "Keep updated").

## Organización en Zotero
Una **colección por estudiante** (`SATG/Cristina`, `SATG/Daniela`, `SATG/Sandra`) + una colección `SATG/Metodología` compartida. Así el mismo PDF puede vivir en dos colecciones sin duplicarse.

## Sistema de resaltado por colores (Smart Note-Taking)

Antes de importar, cada estudiante (y tú como asesor) debe resaltar los PDFs en Zotero con este sistema de **6 colores con significado fijo**:

| Color | Hex | Significado | Para qué sirve en la tesis |
|---|---|---|---|
| 🟡 **Amarillo** | `#ffd400` | Idea principal / argumento central | Notas de lectura (átomos) |
| 🔴 **Rojo** | `#ff6666` | Contradice mi posición / dato que me reta | Discusión, contrastes |
| 🟢 **Verde** | `#5fb236` | Confirma / respalda mi argumento | Marco teórico, antecedentes |
| 🔵 **Azul** | `#2ea8e5` | Definición / concepto clave | Glosario, marco conceptual |
| 🟣 **Morado** | `#a28ae5` | Metodología / diseño / instrumento | Capítulo de metodología |
| 🟠 **Naranja** | `#f19837` | Cita textual que quiero usar literal | Citas directas (con página) |

### Cómo resaltar (flujo de lectura en Zotero)

1. **Abrir el PDF** en el lector integrado de Zotero (doble clic).
2. **Primera pasada (lectura rápida):** resaltar con 🟡 amarillo lo que te parece importante.
3. **Segunda pasada (lectura activa):** cambiar colores según la tabla. ¿Contradice? → 🔴. ¿Es definición? → 🔵. ¿Quieres citar literal? → 🟠.
4. **Escribir notas** (clic derecho → "Add Note to Annotation"): en cada resaltado importante, escribe **tu interpretación** en tus propias palabras. Esto es el Nivel 3 (interno) del [[Método - Notas conectadas para tesis]].
5. **No resaltar todo.** Regla: máximo 10-15 resaltados por paper. Si resaltas todo, no resaltaste nada.

### Por qué importa el color

Cuando importas con la plantilla de abajo, los resaltados se agrupan por color. Así puedes:
- Ver de un vistazo todas las **definiciones** (🔵) de un paper.
- Encontrar rápido lo que **contradice** tu hipótesis (🔴) para la discusión.
- Reunir todas las **citas textuales** (🟠) listas para usar.

---

## Plantilla de importación (Zotero Integration)

### Plantilla básica (sin resaltados)
Guardar como plantilla del comando "Referencia SATG - básica":

```markdown
---
tipo: referencia
citekey: {{citekey}}
autores: {{authors}}
año: {{date | format("YYYY")}}
revista: {{publicationTitle}}
doi: {{DOI}}
estudiante: 
verificada: false
estado_lectura: pendiente
tags: [referencia]
---

# {{title}}

- **Cita APA 7:** (generar desde Zotero)
- **Para qué tesis sirve:** [[]]
- **Idea central:** 
- **Cómo se usa:** (antecedente / marco / método / discusión)

## Abstract
> {{abstractNote}}
```

### Plantilla completa (CON resaltados por color)
Guardar como plantilla del comando "Referencia SATG - con notas":

```markdown
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
```

⚠️ **No usar el filtro `truncate`** en la plantilla Nunjucks: produce error de compatibilidad en Zotero Integration (lección aprendida del flujo original).

### Cómo configurar la plantilla en Obsidian

1. Crea un archivo `01 Plantillas/Zotero - Referencia con notas.md` con el código de arriba.
2. En Obsidian → ⚙️ → **Zotero Integration** → **Import Formats**.
3. Clic en **Add Import Format**.
4. **Name:** `Referencia SATG - con notas`.
5. **Output path:** `02 Tesis en curso/` (después moverás la nota a la carpeta del estudiante).
6. **Template file:** selecciona `01 Plantillas/Zotero - Referencia con notas.md`.
7. **Bibliography style:** APA 7th Edition.
8. Guardar.

## Queries Dataview útiles (pegar donde se necesiten)

Referencias pendientes de leer, por estudiante:
```dataview
TABLE autores, año, estado_lectura
FROM #referencia
WHERE estado_lectura = "pendiente"
SORT estudiante ASC, año DESC
```

Referencias sin verificar (alimenta el [[Protocolo de verificación de referencias]]):
```dataview
TABLE autores, año, doi
FROM #referencia
WHERE verificada = false
```

Conteo de referencias por estudiante:
```dataview
TABLE length(rows) AS "N.º referencias"
FROM #referencia
GROUP BY estudiante
```

## Respaldo
- El vault completo se respalda en Google Drive (carpeta sincronizada) o con el plugin Obsidian Git.
- La biblioteca Zotero se respalda sola si usas cuenta Zotero (300 MB gratis) — los PDF pesados pueden ir por WebDAV o linked files en Drive.

## Solución de problemas (del flujo original)
| Error | Causa | Solución |
|---|---|---|
| Plantilla no renderiza | Filtro `truncate` u otro filtro no soportado | Quitar filtros; usar campos planos |
| Autores mal formateados | Formato de nombre en Zotero | Corregir en Zotero (Apellido, Nombre) antes de importar |
| Obsidian no encuentra Zotero | Zotero cerrado o puerto bloqueado | Abrir Zotero antes de importar |
