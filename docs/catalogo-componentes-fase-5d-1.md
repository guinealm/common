# Fase 5D.1 - Catalogo y contrato de componentes

Fecha: 2026-07-12
Estado: base inicial aprobable para evolucion de componentes

## 1) Objetivo

Definir un catalogo estable de componentes del nucleo visual Jumalenin, con contrato tecnico claro (clases, dependencias, estados y reglas de uso) para reutilizar en Home, Common y futuros sitios.

## 2) Alcance

Incluido en 5D.1:

- inventario de componentes existentes en CSS actuales
- contrato de uso por componente
- reglas de composicion y variantes
- criterios de aceptacion visual y responsive

No incluido en 5D.1:

- nuevas implementaciones visuales complejas
- cambios de branding
- refactor de todos los HTML consumidores

## 3) Dependencias y orden obligatorio

Orden de carga canonico:

1. `jumalenin-core.css`
2. `jumalenin-layout.css`
3. `jumalenin-components.css`

Reglas:

- `core` define tokens y base tipografica.
- `layout` define estructura.
- `components` define piezas reutilizables.
- ningun consumidor debe invertir ese orden.

## 4) Catalogo de componentes (version 1)

### 4.1 Estructura de sitio (layout)

1. `.site-shell`
   - uso: contenedor raiz de pagina completa.

2. `.site-header` + `.header-inner`
   - uso: cabecera global con marca y navegacion.

3. `.site-brand`
   - uso: marca clicable (logo + nombre).

4. `.site-nav`
   - uso: enlaces principales de seccion.

5. `.site-main`
   - uso: contenido principal flexible.

6. `.site-footer` + `.footer-inner`
   - uso: pie global consistente.

7. `.container`
   - uso: ancho maximo y centrado.

8. `.section`, `.section-muted`, `.section-header`
   - uso: bloques de contenido y separacion vertical.

9. `.grid`, `.grid-2`, `.grid-3`, `.grid-4`
   - uso: reticulas responsive.

### 4.2 Hero

1. `.hero`
2. `.hero-inner`
3. `.hero-kicker`
4. `.hero-title`
5. `.hero-lead`
6. `.hero-actions`
7. `.hero-panel`

Uso:

- portada de seccion o landing.
- en movil colapsa a una sola columna (<800px).

### 4.3 Acciones y navegacion

1. `.btn`
2. `.btn-primary`
3. `.btn-secondary`
4. `.btn-accent`

Contrato:

- altura minima 44px (objetivo tactil).
- variantes solo cambian color/superficie; la geometria base viene de `.btn`.

### 4.4 Contenedores de contenido

1. `.card`
2. `.project-card`
3. `.card-footer`
4. `.card-link`

Contrato:

- `.card` es base visual.
- `.project-card` añade comportamiento flex para tarjetas de proyecto.
- acciones secundarias en `.card-link`.

### 4.5 Etiquetas y mensajes

1. `.badge`
2. `.badge-primary`
3. `.badge-accent`
4. `.notice`

Contrato:

- `badge` para metadatos cortos.
- `notice` para mensajes relevantes dentro de seccion.

### 4.6 Listados meta

1. `.meta-list`
2. `.meta-list li`

Contrato:

- lista sin bullets para pares etiqueta-valor o metadatos de ficha.

## 5) Estados y accesibilidad minima

Estados:

- hover visible en enlaces y botones.
- foco visible con `:focus-visible` (definido en core).
- estado activo de navegacion por `[aria-current="page"]` en `.site-nav a`.

Accesibilidad minima obligatoria:

1. foco de teclado visible en elementos interactivos.
2. contraste suficiente en texto principal y enlaces.
3. altura tactil minima para botones y enlaces de navegacion.
4. alt descriptivo en imagenes de marca y contenido.

## 6) Convenciones de nomenclatura

Reglas:

1. prefijo no obligatorio en clases de componente existentes; mantener nombres actuales para compatibilidad.
2. nuevas variantes deben mantener patron `bloque` + `-modificador` (ejemplo: `btn-secondary`).
3. evitar nombres por contexto de pagina (no `home-button`, `support-card`) dentro del nucleo.
4. clases de layout global reservadas para estructura, no para color de negocio.

## 7) Matriz de responsabilidades por CSS

`jumalenin-core.css`:

- tokens
- tipografia base
- elementos globales (`body`, `a`, `h1-h4`, foco)

`jumalenin-layout.css`:

- estructura de pagina
- grid
- breakpoints de layout

`jumalenin-components.css`:

- componentes reutilizables
- variantes de boton/tarjeta/badge/notice

## 8) Criterios de aceptacion de 5D.1

Criterios cumplidos cuando:

1. cualquier pagina consumidora puede montar header/main/footer con clases del contrato.
2. botones, tarjetas, badges y notices se renderizan de forma consistente.
3. el comportamiento responsive funciona en 360, 768 y 1280 de ancho.
4. no aparecen dependencias ocultas a CSS locales para estos componentes.

## 9) Riesgos y mitigacion

1. Riesgo: mezcla de clases legacy y nuevas en un mismo bloque.
   - Mitigacion: migrar por secciones completas, no por lineas sueltas.

2. Riesgo: overrides locales que rompen contrato.
   - Mitigacion: aislar overrides por sitio y documentar motivo.

3. Riesgo: regresiones visuales por orden de carga.
   - Mitigacion: validar orden de CSS en cada consumidor.

## 10) Siguiente paso sugerido (5D.2)

1. Crear pagina de demostracion de componentes en Common:
   - `docs/demo-componentes-5d-2.html` o equivalente.
2. Incluir ejemplos de cada componente y variante.
3. Ejecutar checklist visual y de accesibilidad minima.
4. Publicar guia corta de uso para equipos/futuros cambios.
