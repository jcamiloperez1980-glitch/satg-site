---
tipo: recurso
tags: [sistema, referencias]
---

# Protocolo de verificación de referencias

> Objetivo: que ningún trabajo asesorado llegue a jurados con una referencia inverificable. Diferenciador comercial del SATG: control antialucinaciones en la era de la IA.

## Señales de alerta (referencia posiblemente fabricada por IA)
1. **Base de datos o revista como autor**: "Redalyc (2024)", "Ciencia Latina (2024)", "Scielo (2023)". Las bases indexan, no escriben.
2. **Cita institucional huérfana**: "Universidad X (2022)" sin autores ni título recuperable.
3. **Autor duplicado** en la lista ("Holmes, Porayska-Pomsta y Holmes").
4. Año futuro o volumen/número que no existe en la revista.
5. DOI que no resuelve o resuelve a otro artículo.
6. Título "demasiado perfecto" para la necesidad del párrafo (la IA fabrica el artículo ideal).

## Procedimiento (por cita, ~2 min)
1. **Crossref**: `https://api.crossref.org/works?query.bibliographic=<autor+título>` o buscar en https://search.crossref.org
2. Si no aparece → **OpenAlex**: `https://api.openalex.org/works?search=<título>` (cubre repositorios y revistas latinoamericanas sin DOI Crossref).
3. Si no aparece → **Google Scholar** con título entre comillas.
4. Si no aparece en ninguno → la referencia se marca 🔴 y se retira o sustituye. No se discute: se retira.
5. Toda cita verificada se registra con la [[Plantilla - Referencia anotada]] marcando `verificada: true` y la fuente de verificación.

## Herramientas
- **Crossref** — DOIs oficiales (editorial).
- **OpenAlex** — 250M+ obras, gratuito, con API (usar `mailto=` para el pool rápido).
- **Consensus** — búsqueda semántica de evidencia; útil para ENCONTRAR nuevas referencias, no para verificar exhaustivamente.
- **DOI.org** — resolver el DOI y confirmar que el artículo coincide (título Y autores Y año).

## Regla de calidad de fuente (orientativa)
- Preferir: revistas indexadas (Scopus/WoS/SciELO), editoriales académicas, organismos (UNESCO, OCDE, MEN, Minciencias).
- Usar con moderación y nunca como pilar del marco: *Ciencia Latina*, *LATAM*, revistas multidisciplinares de pago por publicación con revisión débil.
- Fuentes grises (tesis de repositorio): válidas como antecedente local, no como sustento teórico central.
