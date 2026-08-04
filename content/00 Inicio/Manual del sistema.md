---
tipo: manual
tags: [sistema]
---

# Manual del sistema

## Qué es esto

Un vault de Obsidian que convierte cada asesoría de trabajo de grado en un proceso trazable y repetible. Cada tesis vive en su propia carpeta dentro de `02 Tesis en curso/` con cinco notas fijas:

1. **Ficha** — datos maestros, estado y cronograma (frontmatter YAML legible por Dataview).
2. **Diagnóstico** — evaluación de pertinencia, coherencia, alcance y referencias con la [[Rúbrica de diagnóstico de anteproyectos]].
3. **Referencias sugeridas** — bibliografía verificada (DOI comprobado) organizada por eje temático.
4. **Alternativas de proyecto** — 2-3 rutas viables con pros/contras para decidir con el estudiante.
5. **Bitácora de asesorías** — una entrada por sesión, con compromisos y fecha de seguimiento.

## Cómo incorporar una tesis nueva

1. Crea la carpeta `02 Tesis en curso/Nombre - Tema corto/`.
2. Copia las cinco plantillas de `01 Plantillas/` y renómbralas.
3. Llena la Ficha y agenda la sesión de diagnóstico.
4. Aplica la rúbrica → escribe el Diagnóstico → preséntalo al estudiante junto con las Alternativas.
5. Cada sesión posterior se registra en la Bitácora con la plantilla de sesión.

## Plugins recomendados (todos gratuitos)

| Plugin | Para qué |
|---|---|
| **Dataview** | Tablas automáticas del panel de control |
| **Templater** | Insertar plantillas con fecha automática |
| **Zotero Integration** (+ Better BibTeX en Zotero) | Importar referencias con metadatos — ver [[Integración Zotero-Obsidian]] |
| **Kanban** | Tablero visual de fases por tesis (opcional) |
| **Obsidian Git** | Respaldo versionado del vault (opcional) |

El vault funciona sin plugins: todas las vistas tienen equivalente manual con enlaces.

## Respaldo
Sincroniza la carpeta del vault en Google Drive (o usa Obsidian Git). Regla: el respaldo protege también las bitácoras — son tu evidencia ante comités.

## Método de notas conectadas (nuevo)

El vault ahora incluye una capa de **pensamiento conectado** además de la gestión de asesorías. Ver [[Método - Notas conectadas para tesis]] para la guía completa.

Carpeta `Ideas/` dentro de cada tesis → notas de lectura (átomos) + notas permanentes (moléculas) + mapas de contenido (MOC). Plantillas en `01 Plantillas/`.

## Reglas de oro

- Una nota = un propósito. No mezcles diagnóstico con bitácora.
- Todo hallazgo bibliográfico entra con DOI verificado (ver [[Protocolo de verificación de referencias]]).
- El estudiante nunca recibe el vault: recibe PDF/Word exportados de las notas. El vault es tu activo profesional.
- Al cerrar una tesis, mueve su carpeta a `02 Tesis en curso/_Archivo/` y registra las lecciones aprendidas en la ficha.
