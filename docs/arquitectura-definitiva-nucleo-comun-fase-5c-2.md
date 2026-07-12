# Fase 5C.2 - Diseno definitivo del nucleo comun

Fecha: 2026-07-12
Estado: aprobado para ejecucion tecnica en fases posteriores.
Alcance: definir arquitectura final de Common y su contrato con Home. En esta fase no se aplican cambios en Home.

## 1) Decision marco

Se adopta un modelo de nucleo comun centralizado en Common, con consumo remoto desde Home mediante URLs absolutas de dominio comun.

Dominio canonico de assets compartidos:

- https://common.jumalenin.com

Objetivo:

- una sola fuente de verdad para estilos, favicon y logotipos;
- eliminar duplicidades de CSS e imagenes heredadas;
- reducir divergencia entre sitios.

## 2) Arquitectura objetivo (Common)

Raiz publica objetivo de Common:

- opcion operativa A (actual): raiz del proyecto Common
- opcion operativa B (estandar futura): public_html

La decision de raiz publica se fija asi:

- corto plazo: mantener opcion A para evitar ruptura;
- medio plazo: migrar a opcion B solo si se estandariza en todo el ecosistema.

Estructura definitiva del nucleo:

- assets/
  - css/
    - jumalenin-core.css
    - jumalenin-layout.css
    - jumalenin-components.css
  - img/
    - favicon.svg
    - logo.svg
    - logo-horizontal.svg
- index.html
- docs/
  - arquitectura-tecnica-fase-5c-1.md
  - arquitectura-definitiva-nucleo-comun-fase-5c-2.md

Estructura legacy a retirar o archivar tras validacion:

- css/common-*.css
- img/logo-jumalelin.svg
- templates/base.html (si sigue vacio y sin consumidor)

## 3) Contrato CSS definitivo

Orden obligatorio de carga en cualquier consumidor:

1. jumalenin-core.css
2. jumalenin-layout.css
3. jumalenin-components.css

Responsabilidades por archivo:

- jumalenin-core.css
  - tokens globales (color, tipografia, espaciado, bordes, sombras)
  - elementos base (html, body, a, headings, focus)
  - reglas reset/minimas compartidas

- jumalenin-layout.css
  - estructura de pagina (contenedor, shell, header, nav, footer)
  - grid y secciones
  - comportamiento responsive de layout

- jumalenin-components.css
  - componentes reutilizables (btn, card, badge, notice, variantes)
  - estilos de componentes de proyecto
  - no debe redefinir tokens de core

Reglas de dependencia:

- components depende de core y layout.
- layout depende de core.
- core no depende de otros.

## 4) Politica de rutas

### 4.1 Rutas para consumidores (Home y otros sitios)

Usar rutas absolutas al dominio de Common para evitar duplicados locales:

- https://common.jumalenin.com/assets/css/jumalenin-core.css
- https://common.jumalenin.com/assets/css/jumalenin-layout.css
- https://common.jumalenin.com/assets/css/jumalenin-components.css
- https://common.jumalenin.com/assets/img/favicon.svg

### 4.2 Rutas internas de Common

- permitir rutas relativas de raiz para recursos propios en Common:
  - /assets/img/logo-horizontal.svg
- evitar hardcodear rutas locales del filesystem.

## 5) Cabecera, navegacion y pie: contrato estructural

El nucleo no fuerza contenido editorial, pero si contrato de clases y semantica:

- cabecera: .site-header y .header-inner
- navegacion: .site-nav con enlaces semanticos
- pie: .site-footer y .footer-inner

Regla:

- Home puede tener contenido propio, pero debe mapear estas capas para coherencia visual.

## 6) Favicon y logotipos

Canonicos:

- favicon: assets/img/favicon.svg
- logo principal: assets/img/logo.svg
- logo horizontal: assets/img/logo-horizontal.svg

Politica:

- un solo favicon canonico para el ecosistema;
- logo horizontal para cabecera y portada;
- logo cuadrado o simbolo para usos compactos.

## 7) Matriz de conservar / reorganizar / sustituir

Conservar:

- assets/css/jumalenin-core.css
- assets/css/jumalenin-layout.css
- assets/css/jumalenin-components.css
- assets/img/favicon.svg
- assets/img/logo.svg
- assets/img/logo-horizontal.svg

Reorganizar:

- documentar y versionar el contrato CSS en docs;
- preparar carpeta legacy para activos no canonicos.

Sustituir o retirar (tras fase de verificacion):

- css/common-core.css
- css/common-components.css
- css/common-cards.css
- css/common-forms.css
- css/common-nav-footer.css
- img/logo-jumalelin.svg
- templates/base.html vacio (retirar o completar)

## 8) Dependencias de Home respecto al nucleo comun

Contrato esperado de Home:

- no mantener CSS duplicado local si no aporta override funcional;
- cargar solo el trio canonico de Common;
- si se requieren overrides, crear un unico home.css local y cargarlo despues de components.

Regla de overrides:

- permitido: ajustes de layout y contenido especificos de Home.
- no permitido: redefinir tokens base del nucleo sin aprobar cambio en Common.

## 9) Governance tecnico (cambios futuros)

Nivel 1: cambio de tokens o componentes compartidos

- se realiza en Common
- requiere verificacion visual minima en Home y otro sitio consumidor

Nivel 2: cambio exclusivo de Home

- se realiza en Home como override posterior
- no modifica archivos del nucleo comun

Nivel 3: deprecacion de legacy

- requiere inventario de referencias y ventana de limpieza

## 10) Criterios de aceptacion para pasar a fase de aplicacion en Home

- contrato CSS documentado y estable
- lista de activos canonicos cerrada
- lista de legacy candidata a retiro cerrada
- politica de rutas aprobada
- plan de rollback definido

## 11) Resultado de la fase 5C.2

Queda definida la arquitectura definitiva del nucleo comun:

- fuente unica de estilos y branding en Common;
- contrato de carga CSS y responsabilidades por archivo;
- politica de rutas absoluta para consumidores;
- marco de limpieza de duplicidades sin tocar aun Home.
