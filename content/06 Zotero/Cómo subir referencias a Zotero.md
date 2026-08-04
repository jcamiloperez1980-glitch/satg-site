---
tipo: zotero-import
tags: [zotero, sistema]
---

# Cómo subir referencias a Zotero (3 vías, de la más simple a la manual)

> Esta carpeta contiene un archivo por estudiante con sus referencias listas para importar. Regla del SATG: **todo lo que entra a Zotero ya pasó por el [[Protocolo de verificación de referencias]]**.

## Vía 1 — Lista de DOIs con la varita mágica (10 segundos) ⭐
1. Abre Zotero y selecciona (o crea) la colección del estudiante (`SATG/Daniela`, etc.).
2. Clic en la **varita mágica** de la barra (*Add Item(s) by Identifier*).
3. Copia el **bloque completo de DOIs** de la nota del estudiante (p. ej. [[Zotero - Daniela Ortiz]]) y pégalo.
4. Enter → Zotero descarga metadatos completos (autores, revista, volumen, páginas, abstract) de Crossref para todos a la vez.

Acepta DOIs, PMIDs, arXiv IDs e ISBNs mezclados, uno por línea.

## Vía 2 — Archivo .ris (cuando prefieras un solo clic)
1. Zotero → `File → Import…` → selecciona el `.ris` de esta carpeta (p. ej. `Zotero - Daniela Ortiz.ris`).
2. Marca "Place imported collections and items into new collection" para que quede agrupado.
3. Los .ris del SATG traen: tipo, primer autor, año, título, revista, DOI y URL de Consensus. Para completar la lista de autores: clic derecho sobre el ítem → *actualizar metadatos vía DOI* (o botón derecho → "Add Item by Identifier" con su DOI).

## Vía 3 — Registro manual (solo para ítems sin DOI)
En Zotero: botón verde ➕ → *Journal Article* (u otro tipo) y llena estos campos mínimos (los que exige APA 7):

| Campo Zotero | Qué poner |
|---|---|
| Item Type | Journal Article / Report / Book Section / Thesis |
| Title | Título completo tal como aparece en la fuente |
| Author | Un autor por línea, formato `Apellido, Nombre` (botón ➕ para agregar) |
| Publication | Nombre de la revista |
| Date | Año (basta el año) |
| Volume / Issue / Pages | Si se conocen |
| DOI | Vacío (si lo tuviera, usa la Vía 1) |
| URL | Enlace Consensus o de la revista |
| Extra | `Verificada SATG: sí (fecha)` |

Las notas por estudiante incluyen una **tabla de registro manual** con todos estos descriptores ya listos para copiar campo a campo.

## Después de importar (siempre)
- [ ] Arrastrar los ítems a la colección del estudiante.
- [ ] Verificar el conteo contra la nota del vault.
- [ ] Better BibTeX genera las citekeys automáticamente → quedan disponibles para [[Integración Zotero-Obsidian]].

## Archivos en esta carpeta
- [[Zotero - Daniela Ortiz]] — 49 referencias, 100% con DOI (+ `Zotero - Daniela Ortiz.ris`)
- [[Zotero - Cristina López]] — DOIs + tabla de registro manual
- [[Zotero - Sandra Mosquera]] — DOIs + tabla de registro manual
