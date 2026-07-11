# Fase 5B — Definición del núcleo visual común

## 1. Objetivo y alcance

Objetivo de la Fase 5B:

- Definir normativamente el núcleo visual común del ecosistema Jumalenin.
- Clasificar elementos como Obligatorio, Opcional, Propio del subproyecto, Exento o congelado, o Pendiente de decisión.
- Establecer reglas compatibles con la autonomía técnica y visual de proyectos internos.

Ámbito cubierto:

- home.jumalenin.com
- support.jumalenin.com
- staging.jumalenin.com
- common.jumalenin.com
- noturningback.jumalenin.com

Tratamientos especiales en esta norma:

- clima.jumalenin.com (NHMA): Exento o congelado.
- staging/projects/corrupcion/: sometido a reglas generales de identidad, retorno, favicon, cabecera, pie y discreción visual.

Fuente principal utilizada:

- docs/inventario-tecnico-fase-5a.md

Límite de esta fase:

- Documento normativo sin implantación técnica.
- Sin cambios en HTML, CSS, JavaScript, SVG, PNG, ni configuración de despliegue.

## 2. Principios generales

### 2.1 Separación entre estado actual y norma futura

Estado actual (hecho comprobado de Fase 5A):

- Coexisten páginas con capa common remota y subproyectos con estilos propios o embebidos.
- Existen diferencias notables de cabecera, navegación, pie, favicon y uso de logo.

Decisión normativa para el futuro:

- Se adopta un núcleo mínimo común obligatorio para identidad, accesibilidad base y coherencia transversal.
- Se preserva autonomía de subproyectos para su capa funcional y su lenguaje visual específico.

Excepciones justificadas:

- Web congelada (clima/NHMA).
- Páginas históricas o vacías no mantenidas activamente hasta su revisión.

### 2.2 Principio de mínimo común no intrusivo

Decisión normativa:

- Lo obligatorio debe ser ligero, estable y compatible con tablas, mapas, gráficos y aplicaciones.
- No se impone menú global completo ni cabecera pesada en aplicaciones internas.

### 2.3 Principio de autonomía responsable

Decisión normativa:

- Cada subproyecto puede mantener CSS local y componentes propios.
- Todo subproyecto activo debe mantener legibilidad, accesibilidad base, adaptación móvil razonable y vía clara de retorno al área contenedora.

## 3. Matriz resumida obligatorio/opcional/propio

| Elemento | Home | Common | Support principal | Staging principal | Noturningback | Proyectos internos Support/Staging | Corrupción (staging/projects/corrupcion) | Clima/NHMA |
|---|---|---|---|---|---|---|---|---|
| Capa base CSS común | Obligatorio | Obligatorio | Obligatorio | Obligatorio | Obligatorio al activarse | Opcional (si no rompe funcionalidad) | Opcional, con discreción visual | Exento o congelado |
| CSS local complementario | Opcional | Opcional | Opcional | Opcional | Pendiente de decisión | Propio del subproyecto | Propio del subproyecto | Exento o congelado |
| Estilos embebidos/inline nuevos | No recomendado (Pendiente de retiro en fases futuras) | No recomendado | No recomendado | No recomendado | Pendiente de decisión | Propio del subproyecto heredado, con migración futura | Propio heredado permitido por ahora | Exento o congelado |
| Cabecera mínima | Obligatorio | Opcional | Obligatorio | Obligatorio | Obligatorio al activarse | Opcional, sustituible por retorno mínimo | Obligatorio (formato discreto) | Exento o congelado |
| Navegación global completa | Obligatorio en home | Opcional | Opcional | Opcional | Opcional | No necesaria | No necesaria | Exento o congelado |
| Enlace mínimo de retorno | Obligatorio | Opcional | Obligatorio | Obligatorio | Obligatorio al activarse | Obligatorio | Obligatorio | Exento o congelado |
| Pie semántico mínimo | Obligatorio | Opcional | Obligatorio | Obligatorio | Obligatorio al activarse | Opcional (si no interfiere con app) | Obligatorio breve y discreto | Exento o congelado |
| Favicon oficial común | Obligatorio | Obligatorio | Obligatorio | Obligatorio | Obligatorio al activarse | Obligatorio en páginas mantenidas activamente | Obligatorio | Exento o congelado |
| Uso de logo | Opcional recomendado | Opcional recomendado | Opcional recomendado | Opcional recomendado | Pendiente de decisión | Opcional | No necesario si afecta discreción | Exento o congelado |
| Paleta y tipografía del núcleo | Obligatorio para superficie base | Obligatorio | Obligatorio | Obligatorio | Obligatorio al activarse | Propio del subproyecto sobre base legible | Propio del subproyecto con discreción | Exento o congelado |

## 4. Definición detallada de cada elemento

### 4.1 CSS base

Estado actual:

- En common existen tres archivos activos en assets/css: jumalenin-core.css, jumalenin-layout.css y jumalenin-components.css.
- Existen archivos common/css vacíos de línea histórica.
- En support y staging hay subproyectos con CSS local y estilos embebidos.

Decisión normativa:

- Base oficial del núcleo común:
  - common/assets/css/jumalenin-core.css
  - common/assets/css/jumalenin-layout.css
  - common/assets/css/jumalenin-components.css
- Rol normativo por archivo:
  - jumalenin-core.css: normalización básica, tipografía base, variables globales, paleta general, color de fondo/texto, enlaces, foco accesible.
  - jumalenin-layout.css: contenedores, espaciados básicos, estructura semántica de shell, responsive básico.
  - jumalenin-components.css: componentes comunes reutilizables (botones, tarjetas, badges, notices), de uso opcional salvo necesidad explícita.
- Responsabilidades obligatorias de la capa común:
  - normalización básica
  - tipografía base
  - variables globales
  - paleta general
  - color base de fondo y texto
  - estilo base de enlaces
  - contenedores y espaciados base
  - accesibilidad mínima
  - responsive base
- Responsabilidades no obligatorias del núcleo (Propio del subproyecto):
  - tablas de datos avanzadas
  - mapas interactivos
  - diagramas
  - visualizaciones y gráficos
  - formularios especializados de aplicaciones
- CSS local complementario:
  - Permitido en todas las áreas cuando aporte funcionalidad o identidad específica sin romper legibilidad ni accesibilidad base.

Excepciones justificadas:

- Proyectos internos heredados pueden mantener estilos embebidos e inline de forma transitoria.
- No se eliminan ni renombran archivos antiguos en esta fase.

Regla para evitar duplicaciones en fases siguientes:

- Toda regla de base debe existir en un único lugar oficial del núcleo.
- La capa local no debe redefinir la base global salvo justificación funcional del subproyecto.

### 4.2 Cabecera

Estado actual:

- Existen múltiples variantes: cabecera completa, cabeceras técnicas ligeras y páginas sin cabecera normalizada.

Decisión normativa:

- Estructura mínima obligatoria para páginas principales:
  - contenedor semántico header
  - identificación de área o marca Jumalenin
  - título del sitio o proyecto (h1 o equivalente contextual)
  - enlace de retorno válido
- Uso del logo:
  - Opcional recomendado en páginas principales.
  - Opcional en contenido interno.
  - No necesario en aplicaciones internas si compromete claridad o discreción.

Excepciones justificadas:

- Aplicaciones técnicas o internas pueden sustituir cabecera completa por bloque de identificación y retorno mínimo.
- Corrupción requiere cabecera breve y discreta, sin carga visual ornamental.

### 4.3 Navegación

Estado actual:

- Navegación global completa solo en algunas portadas; subproyectos usan navegación ad hoc.

Decisión normativa:

- Niveles de navegación:
  - navegación global entre áreas
  - navegación interna del sitio
  - navegación funcional de aplicación
  - enlace mínimo de retorno
- Obligatoriedad por nivel:
  - Home: navegación global obligatoria.
  - Common: navegación global opcional; al menos retorno o vínculo claro a Home.
  - Support y Staging principales: navegación interna obligatoria y retorno claro a Home.
  - Noturningback (cuando se active): retorno claro obligatorio y navegación interna según contenido.
  - Proyectos internos: no obligatoria navegación global completa; sí obligatorio retorno al contenedor.

Excepciones justificadas:

- Herramientas de pantalla completa, mapas o dashboards pueden omitir menú global si mantienen retorno visible.

### 4.4 Pie

Estado actual:

- Variabilidad alta: pies completos, pies mínimos y páginas sin pie.

Decisión normativa:

- Contenido mínimo obligatorio en páginas principales activas:
  - bloque semántico footer
  - identificación de pertenencia a Jumalenin o al área
  - retorno cuando proceda
- Contenido opcional:
  - fecha de actualización
  - versión
  - autoría
  - nota metodológica
  - avisos técnicos o legales

Excepciones justificadas:

- En aplicaciones internas complejas, el pie puede ser mínimo o no mostrarse si interfiere con la funcionalidad; en ese caso debe existir identificación y retorno en cabecera o barra superior.
- En Corrupción se exige pie breve y discreto.

### 4.5 Favicon

Estado actual:

- Favicon común presente en páginas principales; ausente en muchas internas.

Decisión normativa:

- Favicon oficial: common/assets/img/favicon.svg
- Ruta canónica de referencia para uso transversal: https://common.jumalenin.com/assets/img/favicon.svg
- Obligatoriedad:
  - obligatorio en toda página HTML mantenida activamente
  - obligatorio en páginas principales e internas con mantenimiento
- Páginas antiguas:
  - clasificadas como pendiente de regularización en fases de implantación
- Proyectos internos:
  - obligatorio mantener favicon, aunque conserven autonomía visual
- Variantes futuras:
  - opcionales, solo si se documentan como derivadas oficiales y mantienen coherencia de identidad

Excepciones justificadas:

- Clima/NHMA por estado congelado.

### 4.6 Variantes de logo

Estado actual:

- Variantes detectadas en common: logo principal, logo horizontal, símbolo/logo compacto; además variante dudosa antigua y recurso local no enlazado en home.

Decisión normativa:

- Clasificación oficial de variantes:
  - Logo principal: common/assets/img/logo.svg
    - función: marca completa en contextos de identidad
    - uso: portada de área, bloques de marca, espacios con proporción cuadrada
  - Logo horizontal: common/assets/img/logo-horizontal.svg
    - función: cabeceras, barras superiores y navegación
    - uso: layout horizontal con altura controlada
  - Símbolo o compacto: derivado del principal cuando se requiera espacio reducido
    - uso: iconografía de marca en espacios estrechos
- Variantes antiguas o dudosas:
  - common/img/logo-jumalelin.svg: variante dudosa (vacía) y no oficial
  - sites/home/assets/img/logo-jumalenin.svg.png: recurso local no oficial común

Reglas de uso normativo:

- El logo es opcional, no obligatorio en todas las páginas.
- En aplicaciones internas puede omitirse si perjudica discreción o legibilidad.
- Comportamiento general de tamaño:
  - mantener proporción original
  - evitar alturas invasivas
  - priorizar legibilidad y jerarquía del contenido

### 4.7 Estilos embebidos e inline en legados

Estado actual:

- Uso frecuente en support/projects y staging/projects/salud.

Decisión normativa:

- Se permiten temporalmente como Propio del subproyecto heredado.
- No deben expandirse en páginas nuevas de propósito general.
- Su migración queda para fases de implantación y limpieza, sin obligación inmediata en Fase 5B.

## 5. Reglas por sitio

### 5.1 Home

Decisión normativa:

- Obligatorio:
  - capa base common
  - cabecera semántica mínima
  - navegación global entre áreas
  - pie mínimo semántico
  - favicon oficial
  - retorno claro cuando aplique
- Opcional:
  - logo visible en cabecera
  - metadatos de versión/actualización
- Propio del subproyecto:
  - tarjetas, distribución específica de portada, textos y jerarquía editorial

### 5.2 Common

Decisión normativa:

- Obligatorio:
  - mantenimiento del núcleo CSS oficial
  - favicon oficial
  - identificación clara de biblioteca común
- Opcional:
  - cabecera y pie completos en su portada
  - navegación ampliada
- Propio del subproyecto:
  - documentación visual y páginas de referencia

### 5.3 Support

Decisión normativa:

- Obligatorio en la portada del sitio:
  - base common
  - cabecera y pie mínimos
  - navegación interna clara
  - favicon oficial
- Opcional:
  - navegación global completa
- Propio del subproyecto:
  - lenguaje visual y funcional de proyectos internos

### 5.4 Staging

Decisión normativa:

- Obligatorio en la portada del sitio:
  - base common
  - cabecera y pie mínimos
  - navegación interna clara
  - favicon oficial
- Opcional:
  - navegación global completa
- Propio del subproyecto:
  - identidad de laboratorio y proyectos internos

### 5.5 Noturningback

Estado actual:

- Sin contenido utilizable en páginas HTML inspeccionadas.

Decisión normativa para activación futura:

- Obligatorio al publicarse activamente:
  - favicon oficial
  - retorno claro
  - legibilidad y responsive base
- Pendiente de decisión:
  - nivel de navegación global e interna final
  - patrón de cabecera y pie según naturaleza del contenido

## 6. Reglas para proyectos internos

Ámbito:

- support/projects/
- staging/projects/

Decisión normativa:

- Obligatorio:
  - favicon
  - vía clara de retorno al área contenedora
  - legibilidad mínima
  - accesibilidad base razonable
  - adaptación móvil razonable
- Opcional:
  - uso de capa common en su totalidad
  - mostrar logo
  - incluir navegación global completa
  - pie completo
- Propio del subproyecto:
  - CSS local
  - paleta funcional
  - componentes específicos de tablas, mapas, gráficos, formularios técnicos
  - identidad visual interna del proyecto

Excepciones justificadas:

- Aplicaciones con alta densidad de información pueden priorizar espacio útil sobre ornamentación global.
- Proyectos privados o sensibles deben usar identidad discreta.

## 7. Tratamiento particular de Corrupción

Ámbito limitado:

- staging/projects/corrupcion/

Decisión normativa:

- Obligatorio:
  - identidad mínima coherente con Jumalenin (sin sobrecarga visual)
  - enlace de retorno claro a staging
  - favicon oficial
  - cabecera breve y funcional
  - pie breve y funcional
  - discreción visual
- Opcional:
  - logo visible
  - navegación global o menús ampliados
- Propio del subproyecto:
  - CSS funcional local
  - diseño de tabla y filtros
  - componentes y semántica técnica de la aplicación

Límite explícito:

- Sin cambios editoriales, funcionales, de datos o de lógica en esta fase.

## 8. Tratamiento de clima congelada

Ámbito:

- clima.jumalenin.com (NHMA)

Clasificación normativa:

- Exento o congelado.

Decisión normativa:

- No se aplican obligaciones de implantación en Fase 5B.
- Se mantiene solo como referencia histórica y técnica.

## 9. Decisiones adoptadas

- Se oficializa la base common en tres archivos actuales de common/assets/css.
- Se define un núcleo mínimo obligatorio de identidad y accesibilidad para páginas activas.
- Se mantiene la autonomía de proyectos internos para su capa funcional y visual.
- Se establece favicon común obligatorio en páginas HTML mantenidas activamente.
- Se define retorno claro como requisito transversal.
- Se evita imponer menú global completo o cabecera pesada a aplicaciones internas.
- Se clasifica clima/NHMA como exenta por congelación.
- Se clasifica Corrupción con reglas de identidad mínima y discreción.

## 10. Cuestiones aplazadas

- Plan de migración de estilos embebidos e inline heredados.
- Política de retirada o conservación de archivos CSS antiguos vacíos.
- Criterio final para navegación y estructura de noturningback al activarse.
- Procedimiento de versionado y cacheado de recursos common.
- Catálogo formal de variantes de logo compacto y sus especificaciones exactas de tamaño por breakpoint.

## 11. Criterios de aceptación para cerrar la Fase 5B

Se considerará cerrada la Fase 5B cuando:

1. Exista consenso documental sobre qué es Obligatorio, Opcional, Propio del subproyecto, Exento o congelado, y Pendiente de decisión.
2. Quede aprobada la base oficial de CSS común y su reparto de responsabilidades.
3. Queden aprobadas reglas mínimas de cabecera, navegación, pie, favicon y retorno.
4. Queden aprobadas reglas de autonomía para proyectos internos de support y staging.
5. Quede aprobado el tratamiento específico de Corrupción y clima/NHMA.
6. Se confirme que no se han realizado cambios de implantación técnica durante esta fase.
