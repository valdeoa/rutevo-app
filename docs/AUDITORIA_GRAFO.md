# Graph Report - .  (2026-08-25)

## Corpus Check
- 9 files · ~57,582 words
- Verdict: corpus is large enough that graph structure adds value.

## Summary
- 175 nodes · 247 edges · 12 communities (11 shown, 1 thin omitted)
- Extraction: 76% EXTRACTED · 23% INFERRED · 1% AMBIGUOUS · INFERRED: 58 edges (avg confidence: 0.9)
- Token cost: 495,444 input · 0 output

## Community Hubs (Navigation)
- Incidencias: listado y gestión
- Guard de sesión y navegación
- Acceso y arranque de sesión
- Clientes y plantillas
- Pedidos: datos y fases
- Tabla de pedidos y filtros
- Resiliencia de sesión JWT
- Tablero de estados
- Matriz de agenda
- Marca y página de entrada
- Parseo de CSV
- Previsualización de importación

## God Nodes (most connected - your core abstractions)
1. `rt-gestionar-wire (load and save incident)` - 12 edges
2. `load() - fetch and render client rows` - 12 edges
3. `render (incident table)` - 11 edges
4. `wrap(db) resilient Supabase query proxy` - 8 edges
5. `fetchAll() orders/incidents/clients loader` - 8 edges
6. `wrap (Supabase client retry wrapper)` - 7 edges
7. `rt-board-wire (kanban board wiring)` - 7 edges
8. `New-client modal and insert` - 7 edges
9. `rt-agenda-wire delivery matrix controller` - 6 edges
10. `render() agenda matrix table` - 6 edges

## Surprising Connections (you probably didn't know these)
- `visible (incident filter pipeline)` --semantically_similar_to--> `matchQ (free-text order search)`  [INFERRED] [semantically similar]
  incidencias.html → panel-estados.html
- `Sidebar nav with relative .html hrefs` --semantically_similar_to--> `Sidebar nav with absolute route hrefs`  [AMBIGUOUS] [semantically similar]
  agenda.html → agenda-estado.html
- `render (incident table)` --semantically_similar_to--> `renderBoard`  [INFERRED] [semantically similar]
  incidencias.html → panel-estados.html
- `detail (incident side panel)` --semantically_similar_to--> `showDetail (order detail panel)`  [INFERRED] [semantically similar]
  incidencias.html → panel-estados.html
- `EST (incident state token map)` --semantically_similar_to--> `EST (incident state token map)`  [INFERRED] [semantically similar]
  incidencias.html → gestionar-incidencia.html

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **Supabase session guard and JWT-retry flow** — agenda_rt_guard, agenda_wrap, agenda_isautherr, agenda_reloadonce, agenda_sinsesion, agenda_banner, agenda_estado_phase_update_handler [EXTRACTED 1.00]
- **CSV/Excel order import pipeline** — agenda_estado_readfile, agenda_estado_parsecsv, agenda_estado_splitcsvline, agenda_estado_grouprows, agenda_estado_validate, agenda_estado_counts, agenda_estado_renderpreview, agenda_estado_doimport, agenda_estado_import_headers, pedidos_entrantes_import_modal [EXTRACTED 1.00]
- **Shared order-phase taxonomy (recibido/picking/picked/enviado/incidencia)** — agenda_groups, agenda_slug, agenda_estado_fase, agenda_estado_views, agenda_estado_phaseselector, pedidos_entrantes_entrantes_mode [INFERRED 0.95]
- **Rutevo Supabase session guard pattern (duplicated per page)** — incidencias_rt_guard, gestionar_incidencia_rt_guard, panel_estados_rt_guard, incidencias_wrap, gestionar_incidencia_wrap, panel_estados_wrap [INFERRED 0.95]
- **Rutevo app shell hydration (tenant identity, nav counters, bell alerts, user menu)** — incidencias_rt_hydrate, gestionar_incidencia_rt_hydrate, panel_estados_rt_hydrate [INFERRED 0.95]
- **Incident lifecycle flow: list, filter, open, manage, save state** — incidencias_load, incidencias_visible, incidencias_render, incidencias_open, gestionar_incidencia_rt_gestionar_wire, incidencias_est [EXTRACTED 1.00]
- **Rutevo session/auth flow across login and app pages** — login_conectar, login_signin_handler, login_session_redirect, clientes_plantillas_rt_guard, clientes_plantillas_wrap, clientes_plantillas_isautherr, clientes_plantillas_usermenu [INFERRED 0.85]
- **Client portfolio read/filter/edit/create flow** — clientes_plantillas_load, clientes_plantillas_applyf, clientes_plantillas_sla_editor, clientes_plantillas_cliente_modal, clientes_plantillas_clients_table, clientes_plantillas_chip_filters, clientes_plantillas_search_debounce [EXTRACTED 1.00]
- **Shared Rutevo brand mark across all pages** — index_brand_mark, login_brand_mark, clientes_plantillas_brand_mark [INFERRED 0.95]

## Communities (12 total, 1 thin omitted)

### Community 0 - "Incidencias: listado y gestión"
Cohesion: 0.13
Nodes (25): bad (error state renderer), esc (HTML escaper), EST (incident state token map), fdt (absolute date formatter), Gestionar Incidencia Page, PRIO (priority token map), rt-gestionar-wire (load and save incident), setMsg (save feedback message) (+17 more)

### Community 1 - "Guard de sesión y navegación"
Cohesion: 0.11
Nodes (23): banner discreet session notice, Sidebar nav with absolute route hrefs, Path-slug route dispatch (mode/base resolution), rt-estado-wire order list controller, rt-guard session bootstrap (agenda-estado), rt-hydrate shell identity + alerts (agenda-estado), tenants (Supabase table), VIEWS status view/slug table (+15 more)

### Community 2 - "Acceso y arranque de sesión"
Cohesion: 0.13
Nodes (21): banner() - discreet session notice, window.__db / window.__rtwrap shared client singleton, Never show the mockup with fake data, isAuthErr() - JWT/credential failure detector, Refresh-once-and-retry instead of surfacing raw Postgres errors, reloadOnce() - single-shot reload guard, rt-clients - client portfolio script, rt-guard - session guard bootstrap script (+13 more)

### Community 3 - "Clientes y plantillas"
Cohesion: 0.15
Nodes (20): applyF() - client-side row filter, Bell alert counter (late orders + open incidents), CH / PLANT lookup maps (intake channel and archetype labels), Plantilla / Canal filter chip handlers, New-client modal and insert, clients table (Supabase), esc() - HTML entity escaper, incidents table (Supabase) (+12 more)

### Community 4 - "Pedidos: datos y fases"
Cohesion: 0.15
Nodes (19): decorate(o) order derived-field enrichment, doImport() order + line insertion, FASE order phase dictionary, fetchAll() orders/incidents/clients loader, incidents (Supabase table), linesHTML() order line items table, motiv(o) alert-reason annotation, order_items (Supabase table) (+11 more)

### Community 5 - "Tabla de pedidos y filtros"
Cohesion: 0.12
Nodes (18): applyFilters() column + header-query filter, clients (Supabase table, holds sla_days), computePool() mode-driven order pool, currentSel() day/late narrowing, groupRows() rows grouped into orders, HEADERS/TPL import contract and CSV template, renderBody() order table body, renderTitle() contextual page title (+10 more)

### Community 6 - "Resiliencia de sesión JWT"
Cohesion: 0.14
Nodes (18): banner (session notice), isAuthErr, Silent JWT refresh and single reload (never surface raw Postgres errors), Pantalla honesta sin sesión (never render mock data), reloadOnce, rt-guard session bootstrap (gestionar incidencia), rt-hydrate shell hydration (gestionar incidencia), sinSesion (+10 more)

### Community 7 - "Tablero de estados"
Cohesion: 0.18
Nodes (14): rowg (label/value row builder), rt-hydrate shell hydration (incidencias), atRisk (SLA breach predicate), card (order card renderer), COLS (board column definitions), dueOf (SLA due date), esc (HTML escaper), matchQ (free-text order search) (+6 more)

### Community 8 - "Matriz de agenda"
Cohesion: 0.33
Nodes (7): calcDayW() responsive column width, cell() day count cell renderer, compute() status x day aggregation, GROUPS order lifecycle taxonomy, lateCell() overdue column renderer, num() tabular number span, render() agenda matrix table

### Community 9 - "Marca y página de entrada"
Cohesion: 0.40
Nodes (5): Rutevo brand mark (sidebar), Rutevo brand mark (landing hero), Rutevo coming-soon landing page, Rutevo brand mark (login header), Demo tenant credential prefill buttons

### Community 10 - "Parseo de CSV"
Cohesion: 0.67
Nodes (3): parseCsv() delimiter-sniffing CSV parser, readFile() CSV/XLSX reader with lazy SheetJS, splitCsvLine() quoted-CSV field splitter

## Ambiguous Edges - Review These
- `Sidebar nav with relative .html hrefs` → `Sidebar nav with absolute route hrefs`  [AMBIGUOUS]
  agenda.html · relation: semantically_similar_to
- `Tenant archetype (courier / 3pl / almacen) drives plantilla` → `Operations sidebar navigation`  [AMBIGUOUS]
  clientes-plantillas.html · relation: conceptually_related_to

## Knowledge Gaps
- **48 isolated node(s):** `isAuthErr JWT failure detector`, `reloadOnce single-shot reload guard`, `banner discreet session notice`, `sinSesion honest no-session screen`, `lateCell() overdue column renderer` (+43 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **1 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **What is the exact relationship between `Sidebar nav with relative .html hrefs` and `Sidebar nav with absolute route hrefs`?**
  _Edge tagged AMBIGUOUS (relation: semantically_similar_to) - confidence is low._
- **What is the exact relationship between `Tenant archetype (courier / 3pl / almacen) drives plantilla` and `Operations sidebar navigation`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **Why does `rt-agenda-wire delivery matrix controller` connect `Guard de sesión y navegación` to `Matriz de agenda`, `Pedidos: datos y fases`?**
  _High betweenness centrality (0.051) - this node is a cross-community bridge._
- **Why does `rt-gestionar-wire (load and save incident)` connect `Incidencias: listado y gestión` to `Resiliencia de sesión JWT`, `Tablero de estados`?**
  _High betweenness centrality (0.034) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `rt-gestionar-wire (load and save incident)` (e.g. with `rt-guard session bootstrap (gestionar incidencia)` and `load (fetch incidents)`) actually correct?**
  _`rt-gestionar-wire (load and save incident)` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `wrap(db) resilient Supabase query proxy` (e.g. with `wrap(db) resilient query proxy (agenda-estado)` and `wrap(db) resilient query proxy (pedidos-entrantes)`) actually correct?**
  _`wrap(db) resilient Supabase query proxy` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `isAuthErr JWT failure detector`, `reloadOnce single-shot reload guard`, `banner discreet session notice` to the rest of the system?**
  _48 weakly-connected nodes found - possible documentation gaps or missing edges._