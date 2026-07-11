# Fase 5A — Inventario técnico del estado actual

## 1. Alcance y criterios

Este inventario se ha realizado en modo solo inspección, sin modificar archivos existentes.

Áreas revisadas en local:

- common.jumalenin.com -> c:\jumalenin-ecosistema\common
- home.jumalenin.com -> c:\jumalenin-ecosistema\sites\home
- support.jumalenin.com -> c:\jumalenin-ecosistema\sites\support
- staging.jumalenin.com -> c:\jumalenin-ecosistema\sites\staging
- noturningback.jumalenin.com -> c:\jumalenin-ecosistema\sites\noturningback

Tratamiento especial aplicado:

- clima.jumalenin.com / NHMA: incluido solo como referencia (web congelada).
- staging/projects/corrupcion: revisión limitada a CSS, cabecera, pie, navegación, logotipo y favicon.

Criterios de redacción aplicados:

- Hechos comprobados: observables en archivos inspeccionados.
- Interpretación técnica: lectura de riesgo o consistencia, sin proponer solución.
- "No localizado": cuando no se encuentra el elemento tras revisar el conjunto disponible.
- "No se ha podido verificar": cuando no hay evidencia suficiente en los archivos/rutas disponibles.

## 2. Resumen ejecutivo

Hechos comprobados:

- Existe una base visual común activa en common (`assets/css/jumalenin-*.css`, `assets/img/logo*.svg`, `assets/img/favicon.svg`) cargada por home, support y staging principal mediante URL absoluta `https://common.jumalenin.com/...`.
- En common conviven dos familias CSS:
  - Activa: `assets/css/jumalenin-core.css`, `jumalenin-layout.css`, `jumalenin-components.css`.
  - Antigua/local vacía: `css/common-*.css` (5 archivos de 0 bytes).
- support y staging mezclan páginas alineadas a la capa común con subproyectos heterogéneos (muchos con `<style>` embebido e inline).
- staging mantiene dos líneas: página principal moderna con common remoto y una rama anterior (`index_viejo.html`, `assets/css/common-*.css`, `pages.css`).
- staging/projects/corrupcion utiliza CSS local propio (`assets/css/styles.css`), con cabecera y pie definidos en cada HTML del subproyecto, sin favicon declarado.
- noturningback contiene estructura de carpetas pero HTML vacíos y assets vacíos en el árbol inspeccionado.
- clima/NHMA existe en local como árbol amplio (`public_html` y `v5-test`) y se marca como referencia congelada.

Interpretación técnica (sin propuesta):

- Hay coexistencia de estilos compartidos remotos y estilos locales históricos, con riesgo de divergencia y rutas frágiles por profundidad de carpetas.
- El mayor foco de heterogeneidad está en subproyectos de support y staging (cabeceras, pies, tipografía y modo de carga CSS).

## 3. Inventario de common

### 3.1 Identificación

Hechos comprobados:

- Área: common
- Ruta local: `c:\jumalenin-ecosistema\common`
- Repositorio asociado (remote origin): `https://github.com/guinealm/common.git`
- Dominio: `common.jumalenin.com`
- Estado observado: activo (biblioteca visual compartida)

### 3.2 Archivos CSS

Hechos comprobados:

- CSS activos en `assets/css/`:
  - `jumalenin-core.css` (variables y base)
  - `jumalenin-layout.css` (layout, header/nav/footer, responsive)
  - `jumalenin-components.css` (botones, tarjetas, badges, notice)
- CSS antiguos/locales en `css/`:
  - `common-core.css`, `common-components.css`, `common-cards.css`, `common-forms.css`, `common-nav-footer.css` -> vacíos (0 bytes)
- Carga en `index.html` (orden):
  1. `https://common.jumalenin.com/assets/css/jumalenin-core.css`
  2. `https://common.jumalenin.com/assets/css/jumalenin-layout.css`
  3. `https://common.jumalenin.com/assets/css/jumalenin-components.css`
- Uso de `<style>` en `index.html`: No localizado.
- Uso inline en `index.html`: 1 ocurrencia (`img` con `style="height:56px;width:auto;"`).
- Variables CSS:
  - 24 variables en `:root` de `jumalenin-core.css` (color, sombras, radios, tipografía, espaciado, contenedor).
- `@import`: No localizado en CSS activos inspeccionados.
- `!important`: No localizado en CSS activos inspeccionados.

Interpretación técnica:

- Se observa duplicidad funcional potencial entre `assets/css/jumalenin-*` (activos) y `css/common-*` (vacíos).

### 3.3 Dependencias con common

Hechos comprobados:

- En `common/index.html` se cargan CSS y favicon vía URL absoluta al propio dominio `common.jumalenin.com`.
- Recursos visuales locales presentes:
  - `assets/img/logo.svg`
  - `assets/img/logo-horizontal.svg`
  - `assets/img/favicon.svg`
- Existe copia documental en `docs/arquitectura/jumalenin-identidad-visual-common/common/assets/...` con mismos nombres y tamaños de archivo.

Interpretación técnica:

- Conviven rutas absolutas y copias locales/documentales del mismo recurso.

### 3.4 Cabecera

Hechos comprobados:

- `common/index.html` no define `<header>` estructural; utiliza contenido en `<main>` con logo y título.
- No hay menú de navegación en la página principal de common.

### 3.5 Navegación

Hechos comprobados:

- Menú principal: No localizado.
- Menús secundarios/breadcrumbs: No localizado.

### 3.6 Pie de página

Hechos comprobados:

- `<footer>` en `common/index.html`: No localizado.

### 3.7 Logotipos

Hechos comprobados:

- `assets/img/logo-horizontal.svg` (viewBox `0 0 330 96`)
- `assets/img/logo.svg` (viewBox `0 0 96 96`)
- `img/logo-jumalelin.svg` (0 bytes; contenido no verificable)
- Uso detectado en `index.html`: `/assets/img/logo-horizontal.svg`

Interpretación técnica:

- `img/logo-jumalelin.svg` parece recurso antiguo o incompleto (nombre diferente y vacío).

### 3.8 Favicons

Hechos comprobados:

- Archivo: `assets/img/favicon.svg` (viewBox `0 0 64 64`)
- Declaración en `index.html`:
  - `<link rel="icon" href="https://common.jumalenin.com/assets/img/favicon.svg" type="image/svg+xml">`
- Referencias a iconos de Hostinger: No localizado.

### 3.9 Tipografía y paleta existentes

Hechos comprobados:

- Tipografía declarada en variables: `system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`.
- Paleta principal (variables `--jm-*`):
  - Fondo/superficie: `#f5f7f8`, `#eef2f3`, `#ffffff`, `#f8fafb`
  - Texto: `#1f2933`, `#5f6f7a`, `#ffffff`
  - Primario: `#245b5f`, `#183f42`, `#d9e8e9`
  - Acento: `#c28f2c`, `#8f681d`, `#f3e5c6`
  - Bordes: `#d7dee2`, `#b8c4ca`

### 3.10 Duplicidades e inconsistencias

Hechos comprobados:

- Dos familias CSS en el mismo repositorio (activa vs vacía).
- Recurso `logo-jumalelin.svg` vacío y nombre no alineado con `logo*.svg` en `assets/img`.

## 4. Inventario de home

### 4.1 Identificación

Hechos comprobados:

- Área: home
- Ruta local: `c:\jumalenin-ecosistema\sites\home`
- Repositorio asociado (remote origin): `https://github.com/guinealm/home.git`
- Dominio: `home.jumalenin.com`
- Estado observado: activo (landing de acceso)

### 4.2 Archivos CSS

Hechos comprobados:

- `assets/css/common-core.css` -> vacío (0 bytes)
- `assets/css/site.css` -> vacío (0 bytes)
- `assets/css/home.css` -> contenido CSS local (sin variables `:root`)
- `index.html` carga CSS común remoto (orden):
  1. `https://common.jumalenin.com/assets/css/jumalenin-core.css`
  2. `https://common.jumalenin.com/assets/css/jumalenin-layout.css`
  3. `https://common.jumalenin.com/assets/css/jumalenin-components.css`
- `<style>`: No localizado.
- Inline `style`: No localizado.
- Variables CSS en `home.css`: No localizado.
- `@import`: No localizado.

Interpretación técnica:

- `home.css` contiene estilos de header/main/card/footer pero no está enlazado en `index.html`; coexistencia con dos CSS vacíos de nombre genérico.

### 4.3 Dependencias con common

Hechos comprobados:

- Carga CSS y favicon desde `https://common.jumalenin.com/assets/...`.
- Existe `assets/img/favicon.svg` local y `assets/img/logo-jumalenin.svg.png` local, pero en `index.html` no se referencian.

Interpretación técnica:

- Dependencia principal de recursos remotos common con activos locales paralelos no enlazados.

### 4.4 Cabecera

Hechos comprobados:

- Definida directamente en `index.html` con `<header>` simple (sin clases).
- Contenido: nombre "Jumalenin" y texto descriptivo.
- Logotipo en cabecera: No localizado.

### 4.5 Navegación

Hechos comprobados:

- No existe `<nav>` estructural.
- Navegación por tarjetas (`<a>`) a `clima`, `support`, `staging` (URLs absolutas).
- Enlace a noturningback no activo (sin `href`).

### 4.6 Pie de página

Hechos comprobados:

- `index.html` incluye `<footer>` simple con texto: "Jumalenin · Versión inicial de home".

### 4.7 Logotipos

Hechos comprobados:

- Archivo local: `assets/img/logo-jumalenin.svg.png` (1600x873).
- Uso en HTML: No localizado.

### 4.8 Favicons

Hechos comprobados:

- Declaración en `index.html` a favicon remoto common (`image/svg+xml`).
- Archivo local adicional: `assets/img/favicon.svg` (viewBox `0 0 256 256`) no enlazado.
- Referencias Hostinger: No localizado.

### 4.9 Tipografía y paleta existentes

Hechos comprobados:

- Tipografía efectiva por CSS cargado: common (`system-ui/...`).
- En `home.css` (no enlazado) aparecen: `system-ui, Arial, sans-serif` y colores directos (`#f5f5f5`, `#1f2933`, `#0b5cad`, etc.).

### 4.10 Duplicidades e inconsistencias

Hechos comprobados:

- CSS local con contenido (`home.css`) no enlazado y CSS locales vacíos con nombres similares a common.
- Favicon/logo local coexistiendo con recursos remotos common.

## 5. Inventario de support

### 5.1 Identificación

Hechos comprobados:

- Área: support
- Ruta local: `c:\jumalenin-ecosistema\sites\support`
- Repositorio asociado (remote origin): `https://github.com/guinealm/support.git`
- Dominio: `support.jumalenin.com`
- Estado observado: activo

### 5.2 Archivos CSS

Hechos comprobados:

- Página principal `index.html` carga common remoto (orden core/layout/components) + favicon remoto common.
- CSS local de subproyectos: `projects/assets/css/style.css` (con variables `--dash-*` y `--h-*`).
- Subproyectos con `<style>` embebido (sin CSS externo principal):
  - `projects/Consumo eléctrico/*.html`
  - `projects/Estructura Capital Jóvenes/*.html`
  - `projects/Mapa simbólico Mundial/Mapa simbolico v1..v5.html`
- `projects/herencia.html` y `projects/mapa_mundi.html` enlazan `assets/css/style.css`.
- Uso inline relevante:
  - `projects/herencia.html` (15 ocurrencias)
  - `capital_Chatgpt.html` (13), `capital_gemini.html` (8)
  - `Mapa simbolico` v1..v5 (8-10)
- `@import`: No localizado en CSS externo inspeccionado.
- `!important`: No localizado en CSS externo inspeccionado.

Interpretación técnica:

- Support combina una home alineada con common y un conjunto de subproyectos heterogéneo con estilos embebidos e inline.

### 5.3 Dependencias con common

Hechos comprobados:

- `support/index.html` depende de `https://common.jumalenin.com` para favicon, CSS y logo horizontal.
- Subproyectos (`projects/*.html` y subcarpetas) en general no cargan common remoto.
- Dependencias externas detectadas en subproyectos:
  - `cdn.tailwindcss.com`
  - `cdn.jsdelivr.net/npm/chart.js`
  - `fonts.googleapis.com` (Roboto, Exo 2, Roboto Mono)

### 5.4 Cabecera

Hechos comprobados:

- Variante A (principal): `header.site-header` + `div.header-inner` + logo `site-brand` + `nav.site-nav`.
- Variante B (`herencia`): `header.h-header` con enlace de retorno inline.
- Variante C (`mapa_mundi` y "Mapa simbólico Mundial"): cabeceras `fixed/sticky` con clases utilitarias Tailwind.
- Variante D (Consumo eléctrico, Capital jóvenes): `<header>` sin clases estandarizadas (en varios casos con estilos embebidos).

### 5.5 Navegación

Hechos comprobados:

- Menú principal solo en `support/index.html` (`site-nav`, botones).
- En subproyectos predomina navegación ad hoc (enlaces "volver", anchors internos o ausencia de `<nav>`).
- Breadcrumbs/migas: No localizado.
- Móvil: en subproyectos Tailwind depende de utilidades responsive (`md:*`), en otros casos no se ha podido verificar comportamiento completo sin ejecución visual.

### 5.6 Pie de página

Hechos comprobados:

- `support/index.html` usa `footer.site-footer` con contenido del subdominio.
- `herencia.html`, capital_*.html y mapa simbólico v1..v5 tienen `<footer>` propio.
- `mapa_mundi.html` no muestra `<footer>` estructural explícito en el tramo inspeccionado (No se ha podido verificar pie completo sin lectura íntegra final del archivo).
- Varios HTML de "Consumo eléctrico" no incluyen `<footer>`.

### 5.7 Logotipos

Hechos comprobados:

- Logo principal detectado en `support/index.html`: `https://common.jumalenin.com/assets/img/logo-horizontal.svg`.
- En subproyectos no se localizaron `src` con patrón `logo|brand`.

### 5.8 Favicons

Hechos comprobados:

- Solo `support/index.html` declara favicon (remoto common, `image/svg+xml`).
- En subproyectos revisados no se localizó `<link rel="icon">`.
- Referencias Hostinger: No localizado.

### 5.9 Tipografía y paleta existentes

Hechos comprobados:

- Home support: tipografía y paleta heredadas de common (`--jm-*`).
- `projects/assets/css/style.css` define variables:
  - Dashboard: `--dash-bg #0B1120`, `--dash-card #151e32`, `--dash-text #e2e8f0`, `--dash-accent #3B82F6`.
  - Herencia: `--h-primary #2c3e50`, `--h-accent-gold #f1c40f`, `--h-accent-blue #3498db`, `--h-accent-green #27ae60`, `--h-alert #e74c3c`, etc.
- Fuentes externas: Inter, Exo 2, Roboto Mono, Roboto (según subproyecto).

### 5.10 Duplicidades e inconsistencias

Hechos comprobados:

- Multiplicidad de patrones de cabecera/pie entre subproyectos.
- Mezcla de CSS externo único (`style.css`) con estilos embebidos por página.
- Diferentes sistemas de navegación y naming de componentes según proyecto.

## 6. Inventario de staging

### 6.1 Página principal de staging

#### Identificación

Hechos comprobados:

- Área: staging principal
- Ruta local: `c:\jumalenin-ecosistema\sites\staging\index.html`
- Repositorio asociado (remote origin): `https://github.com/guinealm/staging.git`
- Dominio: `staging.jumalenin.com`
- Estado observado: interno (texto descriptivo de confidencialidad en portada)

#### CSS, cabecera, navegación, pie, logo, favicon

Hechos comprobados:

- Carga common remoto (orden core/layout/components) y favicon common.
- Cabecera `site-header` con `site-brand` (logo common) y `site-nav`.
- Pie `site-footer` presente.
- Navegación por botones a proyectos y documentación.
- `<style>` e inline: No localizado.

### 6.2 Subproyectos generales

Hechos comprobados:

- `index_viejo.html` usa CSS local:
  1. `./assets/css/common-core.css`
  2. `./assets/css/common-nav-footer.css`
  3. `./assets/css/pages.css`
- `index_viejo.html` no declara favicon.
- `index_viejo.html` tiene `<header>` simple sin `<footer>`.
- `projects/salud/index.html` usa `<style>` embebido y fuente externa Inter; no favicon localizado.
- `projects/salud/index_malo.html` usa CSS relativo a `../../assets/css/...` (sin favicon).

CSS locales staging:

- `assets/css/common-core.css` (mínimo; regla base `body`)
- `assets/css/common-nav-footer.css` (mínimo; `header,footer` y `a`)
- `assets/css/pages.css` (`:root` con 16 variables de color/fases)

Interpretación técnica:

- Coexisten rama principal integrada con common remoto y rama local histórica reutilizada por páginas internas.

### 6.3 Corrupción — revisión visual y estructural limitada

(Se ha respetado la limitación: solo CSS, cabecera, pie, navegación, logo y favicon.)

Hechos comprobados:

- Rutas inspeccionadas:
  - `projects/corrupcion/index.html`
  - `projects/corrupcion/index-db.html`
  - `projects/corrupcion/index-pre-fase6c-json-backup.html`
  - `projects/corrupcion/assets/css/styles.css`
- CSS:
  - Todos los HTML del subproyecto cargan `assets/css/styles.css`.
  - `styles.css` define variables (`--bg`, `--panel`, `--text`, fases y gravedad), layout de tabla, etiquetas y media query móvil.
  - `@import`: No localizado.
  - `!important`: No localizado.
- Cabecera:
  - `<header class="site-header">` en las tres variantes.
  - Incluye enlace "Volver a Staging" (URL absoluta al dominio staging), título y texto contextual.
- Navegación:
  - No hay `<nav>` estructural.
  - Navegación principal detectada: enlace de retorno a staging.
- Pie:
  - `<footer class="site-footer">` presente en las tres variantes.
- Logo:
  - No localizado en HTML del subproyecto.
- Favicon:
  - No localizado en HTML del subproyecto.

Interpretación técnica:

- Subproyecto autocontenido visualmente con CSS local específico, desacoplado del set common remoto en favicon/logo.

## 7. Inventario de noturningback

### 7.1 Identificación

Hechos comprobados:

- Área: noturningback
- Ruta local: `c:\jumalenin-ecosistema\sites\noturningback`
- Repositorio Git asociado: No localizado
- Dominio: `noturningback.jumalenin.com`
- Estado observado: en construcción (estructura presente, contenidos vacíos en HTML)

### 7.2 CSS, cabecera, navegación, pie, logo, favicon

Hechos comprobados:

- `index.html` y `pages/01..06` existen pero están vacíos.
- `assets/css`, `assets/img`, `assets/js` están presentes como carpetas pero vacías.
- CSS enlazado en HTML: No se ha podido verificar (HTML sin contenido).
- Cabecera/pie/navegación/logo/favicon: No se ha podido verificar.

Interpretación técnica:

- No hay evidencia utilizable para evaluar consistencia visual actual.

## 8. Referencia de clima / NHMA — web congelada

Hechos comprobados:

- Ruta local inspeccionada: `c:\jumalenin-ecosistema\sites\NHMA\public_html`
- Repositorio Git asociado: No localizado
- Dominio/subdominio de referencia: clima.jumalenin.com / NHMA
- Estado: congelado (referencia únicamente)
- Se detecta árbol amplio con:
  - HTML múltiples (`index`, `pagina*`, `novedades`, `status`)
  - CSS (`assets/css/base.css`, `common-core.css`, `common-nav-footer.css`, `common.css`, `pages.css`)
  - réplica `v5-test` con estructura similar.

Interpretación técnica:

- No se plantean intervenciones sobre NHMA en esta fase, por criterio explícito de web congelada.

## 9. Tabla comparativa

| Área | CSS común | CSS local | Cabecera | Pie | Logo | Favicon | Navegación | Observaciones |
|---|---|---|---|---|---|---|---|---|
| common | Sí (`jumalenin-*`) | Sí (`common-*` vacíos) | No localizado como bloque `<header>` | No localizado | Sí (`logo.svg`, `logo-horizontal.svg`) | Sí (`assets/img/favicon.svg`) | Menú no localizado | Conviven capas CSS activa y antigua vacía |
| home | Sí (remoto common) | Sí (`home.css` + 2 vacíos) | `<header>` simple | `<footer>` simple | Archivo local no enlazado | Sí (remoto common; local adicional no enlazado) | Enlaces en cards, sin `<nav>` | Dependencia remota + activos locales paralelos |
| support | Sí (solo `index.html`) | Sí (`projects/assets/css/style.css` + `<style>` en múltiples páginas) | Varias implementaciones | Varias implementaciones / ausencia en algunos HTML | Sí en `index.html` (logo common) | Sí solo en `index.html` | Mixta (site-nav en home + navegación ad hoc en subproyectos) | Alta heterogeneidad entre subproyectos |
| staging | Sí (index principal) | Sí (`assets/css/*`, `corrupcion/styles.css`, estilos embebidos en salud) | Varias (site-header y header simple) | Presente en index principal y corrupción; ausente en otras | Sí en index principal (logo common) | Sí en index principal; no en muchas páginas internas | Mixta (site-nav en index; enlaces sueltos en otros) | Coexistencia de rama común moderna y rama local heredada |
| noturningback | No se ha podido verificar | No se ha podido verificar | No se ha podido verificar | No se ha podido verificar | No se ha podido verificar | No se ha podido verificar | No se ha podido verificar | HTML y assets vacíos |
| clima/NHMA (referencia congelada) | No se ha podido verificar en detalle | Sí (`assets/css/*.css` + `v5-test`) | No se ha podido verificar en detalle | No se ha podido verificar en detalle | No se ha podido verificar en detalle | No se ha podido verificar en detalle | No se ha podido verificar en detalle | Referencia congelada; sin propuesta de intervención |

## 10. Duplicidades e inconsistencias

Hechos comprobados:

- `common`: duplicidad de intención entre `assets/css/jumalenin-*` (activos) y `css/common-*` (vacíos).
- `home`: CSS local (`home.css`) coexistiendo con carga exclusiva de CSS remoto common.
- `staging`: `index.html` usa common remoto, mientras `index_viejo.html` y `projects/salud/index_malo.html` usan CSS local relativo.
- `support`: coexistencia de patrón common en home con subproyectos altamente dispares (Tailwind/CDN, CSS local compartido, `<style>` embebido por página).
- Favicon consistente solo en páginas principales `common/home/support/staging`; ausente en gran parte de subpáginas.
- Logo consistente en páginas principales (`logo-horizontal.svg` remoto common), ausente en la mayoría de subproyectos.
- Recursos locales aparentemente abandonados o no conectados:
  - `common/img/logo-jumalelin.svg` (0 bytes)
  - `home/assets/css/common-core.css` y `home/assets/css/site.css` (vacíos)

## 11. Dependencias técnicas

Hechos comprobados:

- Dependencias remotas a common:
  - `https://common.jumalenin.com/assets/css/jumalenin-core.css`
  - `https://common.jumalenin.com/assets/css/jumalenin-layout.css`
  - `https://common.jumalenin.com/assets/css/jumalenin-components.css`
  - `https://common.jumalenin.com/assets/img/favicon.svg`
  - `https://common.jumalenin.com/assets/img/logo-horizontal.svg`
- Dependencias externas de terceros en subproyectos:
  - `https://cdn.tailwindcss.com`
  - `https://cdn.jsdelivr.net/npm/chart.js`
  - `https://fonts.googleapis.com/...`
- Dependencias por ruta relativa en staging antiguo y salud/index_malo:
  - `./assets/css/...`
  - `../../assets/css/...`

Interpretación técnica:

- El sistema actual mezcla dependencia central remota, recursos relativos locales y CDNs de terceros con diferentes niveles de acoplamiento.

## 12. Riesgos para la futura unificación

(Descripción de riesgo únicamente; sin solución.)

- Dependencias remotas directas a common en páginas críticas: caída o cambio de ruta impacta home/support/staging principal.
- Rutas relativas con distinta profundidad (`./`, `../../`, `assets/...`): riesgo de rotura al reorganizar carpetas.
- Colisiones de naming potenciales entre clases comunes (`site-header`, `site-footer`, `.card`, `.tag`) y clases locales de subproyectos.
- Alto uso de `<style>` embebido e inline en subproyectos de support: complica centralización y trazabilidad.
- Diferencias de arquitectura (common moderno vs ramas locales heredadas) pueden generar divergencias de comportamiento responsive.
- Ausencia de favicon/logo en muchas páginas internas: riesgo de inconsistencia visual al consolidar navegación transversal.
- Dependencias externas CDN/fuentes: riesgo de disponibilidad, cambios de versión y variabilidad de caché.
- Archivos vacíos con nombres funcionales activos (`common-*`, `site.css`, etc.): riesgo de confusión operativa en futuras fases.

## 13. Archivos revisados

### 13.1 common

- `c:\jumalenin-ecosistema\common\index.html`
- `c:\jumalenin-ecosistema\common\assets\css\jumalenin-core.css`
- `c:\jumalenin-ecosistema\common\assets\css\jumalenin-layout.css`
- `c:\jumalenin-ecosistema\common\assets\css\jumalenin-components.css`
- `c:\jumalenin-ecosistema\common\css\common-core.css`
- `c:\jumalenin-ecosistema\common\css\common-components.css`
- `c:\jumalenin-ecosistema\common\css\common-cards.css`
- `c:\jumalenin-ecosistema\common\css\common-forms.css`
- `c:\jumalenin-ecosistema\common\css\common-nav-footer.css`
- `c:\jumalenin-ecosistema\common\assets\img\favicon.svg`
- `c:\jumalenin-ecosistema\common\assets\img\logo.svg`
- `c:\jumalenin-ecosistema\common\assets\img\logo-horizontal.svg`
- `c:\jumalenin-ecosistema\common\img\logo-jumalelin.svg`

### 13.2 home

- `c:\jumalenin-ecosistema\sites\home\index.html`
- `c:\jumalenin-ecosistema\sites\home\assets\css\home.css`
- `c:\jumalenin-ecosistema\sites\home\assets\css\common-core.css`
- `c:\jumalenin-ecosistema\sites\home\assets\css\site.css`
- `c:\jumalenin-ecosistema\sites\home\assets\img\favicon.svg`
- `c:\jumalenin-ecosistema\sites\home\assets\img\logo-jumalenin.svg.png`

### 13.3 support

- `c:\jumalenin-ecosistema\sites\support\index.html`
- `c:\jumalenin-ecosistema\sites\support\projects\assets\css\style.css`
- `c:\jumalenin-ecosistema\sites\support\projects\herencia.html`
- `c:\jumalenin-ecosistema\sites\support\projects\mapa_mundi.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Consumo eléctrico\Energía.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Consumo eléctrico\preview android 6.0.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Consumo eléctrico\preview android2 v4.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Consumo eléctrico\preview Energía 1.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Consumo eléctrico\preview Energía 2.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Estructura Capital Jóvenes\capital_Chatgpt.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Estructura Capital Jóvenes\capital_gemini.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Mapa simbólico Mundial\Mapa simbolico v1.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Mapa simbólico Mundial\Mapa simbolico v2.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Mapa simbólico Mundial\Mapa simbolico v3.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Mapa simbólico Mundial\Mapa simbolico v4.html`
- `c:\jumalenin-ecosistema\sites\support\projects\Mapa simbólico Mundial\Mapa simbolico v5.html`

### 13.4 staging

- `c:\jumalenin-ecosistema\sites\staging\index.html`
- `c:\jumalenin-ecosistema\sites\staging\index_viejo.html`
- `c:\jumalenin-ecosistema\sites\staging\assets\css\common-core.css`
- `c:\jumalenin-ecosistema\sites\staging\assets\css\common-nav-footer.css`
- `c:\jumalenin-ecosistema\sites\staging\assets\css\pages.css`
- `c:\jumalenin-ecosistema\sites\staging\projects\salud\index.html`
- `c:\jumalenin-ecosistema\sites\staging\projects\salud\index_malo.html`
- `c:\jumalenin-ecosistema\sites\staging\projects\corrupcion\index.html`
- `c:\jumalenin-ecosistema\sites\staging\projects\corrupcion\index-db.html`
- `c:\jumalenin-ecosistema\sites\staging\projects\corrupcion\index-pre-fase6c-json-backup.html`
- `c:\jumalenin-ecosistema\sites\staging\projects\corrupcion\assets\css\styles.css`

### 13.5 noturningback

- `c:\jumalenin-ecosistema\sites\noturningback\index.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\01-esta-cambiando.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\02-hace-dano.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\03-por-que.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\04-que-debe-hacer-el-mundo.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\05-que-puedo-hacer-yo.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\pages\06-como-nos-enganan.html` (vacío)
- `c:\jumalenin-ecosistema\sites\noturningback\assets\css\` (carpeta vacía)
- `c:\jumalenin-ecosistema\sites\noturningback\assets\img\` (carpeta vacía)
- `c:\jumalenin-ecosistema\sites\noturningback\assets\js\` (carpeta vacía)

### 13.6 clima/NHMA (referencia congelada)

- `c:\jumalenin-ecosistema\sites\NHMA\public_html\index.html`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\novedades.html`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\status.html`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\pagina*.html` (conjunto detectado)
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\assets\css\base.css`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\assets\css\common-core.css`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\assets\css\common-nav-footer.css`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\assets\css\common.css`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\assets\css\pages.css`
- `c:\jumalenin-ecosistema\sites\NHMA\public_html\v5-test\...` (estructura equivalente detectada)
