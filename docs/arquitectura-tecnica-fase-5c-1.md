# Fase 5C.1 - Revision tecnica de Common y Home

Fecha: 2026-07-12
Alcance: solo revision tecnica. No se han modificado archivos funcionales.

## 1) Estado de rutas solicitadas

- common/public_html: no existe en el arbol local actual.
- home/public_html: no existe en el arbol local actual.

Rutas activas equivalentes detectadas:

- Common activo local: C:/jumalenin-ecosistema/common
- Home activo local: C:/jumalenin-ecosistema/sites/home

## 2) Estructura actual

### Common

Estructura principal:

- assets/css
- assets/img
- css
- docs
- img
- js
- templates
- index.html

Observacion: coexisten dos capas de estilos y recursos:

- capa actual de marca compartida en assets/css y assets/img
- capa heredada en css e img

### Home

Estructura principal:

- assets/css
- assets/img
- index.html

Observacion: assets/js existe pero sin contenido.

## 3) CSS existentes y orden de carga

### Common (index principal)

Orden actual de carga:

1. https://common.jumalenin.com/assets/css/jumalenin-core.css
2. https://common.jumalenin.com/assets/css/jumalenin-layout.css
3. https://common.jumalenin.com/assets/css/jumalenin-components.css

Diagnostico:

- orden correcto base -> layout -> componentes.
- se cargan por URL absoluta al propio dominio common.

### Home (index de sitio)

Orden actual de carga:

1. https://common.jumalenin.com/assets/css/jumalenin-core.css
2. https://common.jumalenin.com/assets/css/jumalenin-layout.css
3. https://common.jumalenin.com/assets/css/jumalenin-components.css

Diagnostico:

- Home depende de Common para estilos.
- Home tiene CSS locales en assets/css, pero no se cargan actualmente.

## 4) Cabecera, navegacion y pie

### Common

- Cabecera: no hay bloque header semantico; hay contenido principal en main.
- Navegacion: no hay nav.
- Pie: no hay footer.

### Home

- Cabecera: bloque header con titulo y texto.
- Navegacion: no hay nav explicito; hay tarjetas con enlaces en main.
- Pie: bloque footer simple.

## 5) Favicon y logotipos

### Common

- Favicon cargado: /assets/img/favicon.svg (referencia absoluta de dominio en index).
- Logotipo usado: /assets/img/logo-horizontal.svg.
- Otros logos presentes: assets/img/logo.svg y img/logo-jumalelin.svg.

### Home

- Favicon cargado desde Common: https://common.jumalenin.com/assets/img/favicon.svg
- En el index actual no hay img de logotipo.
- Archivo local presente no usado en index: assets/img/logo-jumalenin.svg.png

## 6) Rutas absolutas y relativas

### Common

- CSS y favicon por rutas absolutas de dominio.
- Imagen principal con ruta relativa de raiz /assets/img/logo-horizontal.svg

### Home

- CSS y favicon por rutas absolutas de dominio common.jumalenin.com
- Enlaces de tarjetas por rutas absolutas a subdominios

## 7) Duplicidades y elementos potencialmente antiguos

Hallazgos:

- No existe public_html ni para common ni para home en las rutas solicitadas.
- Doble arbol CSS en Common:
  - assets/css/jumalenin-*.css (activo)
  - css/common-*.css (sin uso detectado en index actual)
- Doble arbol de imagenes en Common:
  - assets/img (activo)
  - img (parcialmente legado)
- Home contiene CSS local no cargado:
  - assets/css/home.css (contenido)
  - assets/css/common-core.css (vacio)
  - assets/css/site.css (vacio)
- Home contiene logo local no referenciado:
  - assets/img/logo-jumalenin.svg.png
- templates/base.html esta vacio.

## 8) Recomendacion tecnica (conservar, reorganizar, sustituir)

### Conservar

- assets/css/jumalenin-core.css
- assets/css/jumalenin-layout.css
- assets/css/jumalenin-components.css
- assets/img/favicon.svg
- assets/img/logo-horizontal.svg
- index actual de Common y Home

### Reorganizar

- Definir una convencion unica de raiz publica:
  - opcion A: usar raiz de proyecto como publica
  - opcion B: estandarizar a public_html para todos los sitios
- Si se adopta opcion B, planificar migracion controlada en ventana tecnica.

### Sustituir o archivar

- En Common, mover css/common-*.css a carpeta de legado documentada, si se confirma no uso.
- En Common, mover img/logo-jumalelin.svg a legado si no se referencia.
- En Home, archivar assets/css/home.css, assets/css/common-core.css y assets/css/site.css si no se reactivan.
- En Home, archivar assets/img/logo-jumalenin.svg.png si no se va a usar en el index.
- Mantener templates/base.html vacio solo si esta reservado; en caso contrario, eliminar o completar con plantilla canonica.

## 9) Conclusion breve

La arquitectura actual funciona sobre rutas activas sin public_html en Common y Home. El nucleo visual compartido se consume correctamente desde Common con orden CSS coherente. El principal margen de mejora esta en limpieza de legado local (CSS e imagenes no usadas), documentacion de raiz publica estandar y consolidacion de estructura para siguientes fases.
