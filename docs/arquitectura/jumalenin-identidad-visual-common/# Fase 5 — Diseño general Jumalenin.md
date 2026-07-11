# Fase 5 — Diseño general Jumalenin

## 5A — Definición de elementos comunes

### 1. Alcance

La línea visual común se aplicará progresivamente a:

* home.jumalenin.com
* support.jumalenin.com
* staging.jumalenin.com
* common.jumalenin.com
* noturningback.jumalenin.com

Queda fuera:

* clima.jumalenin.com, por tratarse de una web congelada.

El subproyecto Corrupción no se rediseñará funcionalmente. Solo podrá recibir ajustes generales de cabecera, pie, navegación, tipografía o discreción visual.

---

## 2. Principio general

Jumalenin no debe parecer una colección de webs idénticas, sino un ecosistema reconocible.

Todos los ámbitos compartirán:

* identidad gráfica;
* criterios tipográficos;
* estructura básica de cabecera y pie;
* estilos base de botones, enlaces y tarjetas;
* reglas comunes de anchura, espaciado y adaptación móvil.

Cada área conservará:

* su función;
* su jerarquía de contenidos;
* su tono visual;
* los componentes específicos que necesite.

---

## 3. Elementos que deben ser comunes

### 3.1 Favicon y logotipo

Debe existir una única identidad principal Jumalenin:

* `favicon.svg` común para todos los subdominios;
* logotipo principal Jumalenin;
* versión reducida del logotipo para cabeceras pequeñas;
* nombre del área como complemento, no como logotipo independiente.

Ejemplos:

* Jumalenin · Home
* Jumalenin · Support
* Jumalenin · Staging
* Jumalenin · No Turning Back

El favicon debe cargarse desde una ruta estable de `common`, evitando copias distintas salvo que técnicamente sea necesario.

---

### 3.2 Paleta

Debe definirse una paleta común reducida:

* color principal de identidad;
* color secundario;
* color de fondo general;
* color de superficie para tarjetas y bloques;
* color de texto principal;
* color de texto secundario;
* color de bordes;
* colores de estado: información, aviso, éxito y error.

Las áreas podrán usar una variante o acento propio, pero sin sustituir la paleta general.

Propuesta conceptual:

* Home: identidad general neutra.
* Support: acento más abierto o público.
* Staging: acento más discreto y técnico.
* Common: presentación neutra del sistema.
* No Turning Back: acento climático propio, integrado en la identidad general.

No conviene asignar ahora colores definitivos sin revisar los CSS existentes.

---

### 3.3 Tipografía

Debe existir una única familia tipográfica principal para:

* cuerpo de texto;
* navegación;
* botones;
* formularios.

También deben quedar normalizados:

* tamaño del texto base;
* niveles de títulos `h1` a `h4`;
* altura de línea;
* anchura máxima de los párrafos;
* peso de títulos y enlaces;
* tamaños mínimos en móvil.

Los proyectos no deberían definir tipografías propias salvo excepción justificada.

---

### 3.4 Cabecera

La cabecera común debe contener, como mínimo:

1. identidad Jumalenin;
2. nombre o función del área;
3. navegación principal;
4. adaptación móvil.

Estructura propuesta:

* izquierda: logotipo o nombre Jumalenin;
* centro o continuación: nombre del área;
* derecha: navegación;
* móvil: cabecera compacta con navegación simplificada.

No todas las áreas necesitan exactamente los mismos enlaces.

#### Navegación común mínima

* Inicio Jumalenin
* Área actual
* Proyectos o contenidos principales
* Enlace de retorno cuando se entra en un subproyecto

La cabecera no debe ocupar demasiado espacio ni competir con el contenido.

---

### 3.5 Pie de página

Debe existir un pie común sencillo con:

* identidad Jumalenin;
* nombre del área;
* enlace a la página principal;
* fecha o año;
* aviso de uso interno cuando corresponda;
* enlaces adicionales solo cuando sean necesarios.

Ejemplo para staging:

> Jumalenin · Staging
> Área de trabajo y proyectos en desarrollo. Uso interno.

No conviene llenar el pie con enlaces repetidos o información que ya aparece en la cabecera.

---

### 3.6 Navegación

Deben diferenciarse tres niveles:

#### Nivel 1 — Ecosistema

Permite pasar entre:

* Home
* Support
* Staging
* No Turning Back

Common no necesita tener el mismo protagonismo, porque actúa principalmente como infraestructura compartida.

#### Nivel 2 — Área

Navegación propia de support, staging o noturningback.

#### Nivel 3 — Proyecto

Navegación interna de cada proyecto, por ejemplo Corrupción.

La navegación del ecosistema no debe mezclarse visualmente con los controles funcionales de cada aplicación.

---

### 3.7 Botones

Debe existir una definición común para:

* botón principal;
* botón secundario;
* botón discreto;
* botón de advertencia;
* botón desactivado;
* botón con icono;
* enlace presentado como botón.

Reglas generales:

* misma altura y redondeado;
* contraste suficiente;
* estados `hover`, `focus` y `disabled`;
* tamaño táctil adecuado en móvil;
* evitar que cualquier enlace se convierta innecesariamente en botón.

---

### 3.8 Tarjetas

Las tarjetas deben compartir:

* borde o sombra moderada;
* radio de esquina;
* espaciado interior;
* jerarquía de título, descripción y acción;
* comportamiento uniforme en escritorio y móvil.

Se deben definir al menos:

* tarjeta de proyecto;
* tarjeta informativa;
* tarjeta de estado;
* tarjeta compacta.

No todos los bloques deben convertirse en tarjetas. Su uso debe reservarse para contenidos independientes o seleccionables.

---

### 3.9 Estructura de páginas

Las páginas generales deberían usar una estructura común:

1. cabecera;
2. bloque principal o presentación;
3. contenido dentro de un contenedor de anchura limitada;
4. secciones claramente separadas;
5. pie.

Elementos compartidos:

* ancho máximo del contenido;
* márgenes laterales;
* espaciado vertical;
* tratamiento de títulos;
* fondos de sección;
* separación entre bloques.

Debe evitarse que cada página defina de nuevo sus propios márgenes, anchos y reglas responsivas.

---

### 3.10 Estructura de páginas de proyectos

Las páginas de entrada de proyectos deberían incluir:

* nombre del proyecto;
* descripción breve;
* estado: activo, experimental, archivado o en construcción;
* acceso principal;
* información secundaria solo si aporta valor;
* enlace claro de retorno al área correspondiente.

Para staging debe existir además una forma discreta de indicar:

* uso interno;
* proyecto experimental;
* contenido no destinado a difusión;
* estado de desarrollo.

Estas indicaciones no deben dominar visualmente la página.

---

## 4. Elementos que no deben hacerse comunes

Deben mantenerse dentro de cada proyecto:

* tablas de datos;
* filtros;
* formularios;
* mapas;
* gráficos;
* fichas;
* buscadores;
* controles específicos;
* estructuras editoriales propias;
* lógica JavaScript;
* estilos estrictamente funcionales.

Common podrá proporcionar estilos base, pero no debe convertirse en un CSS monolítico que contenga todas las excepciones de todos los proyectos.

---

## 5. Organización recomendada en common

Propuesta inicial:

```text
common/
├── assets/
│   ├── img/
│   │   ├── favicon.svg
│   │   ├── logo.svg
│   │   └── logo-compacto.svg
│   └── icons/
├── css/
│   ├── jumalenin-core.css
│   ├── jumalenin-layout.css
│   ├── jumalenin-components.css
│   ├── jumalenin-navigation.css
│   └── jumalenin-utilities.css
└── js/
    └── jumalenin-navigation.js
```

Función de cada archivo:

* `jumalenin-core.css`: variables, colores, tipografía y normalización.
* `jumalenin-layout.css`: contenedores, secciones, cabecera, pie y rejillas.
* `jumalenin-components.css`: tarjetas, botones, avisos y etiquetas.
* `jumalenin-navigation.css`: menús y navegación móvil.
* `jumalenin-utilities.css`: clases auxiliares muy limitadas.
* `jumalenin-navigation.js`: solo si es necesario para el menú móvil.

Antes de crear nuevos archivos debe revisarse la estructura existente en common para no duplicar lo ya desarrollado.

---

## 6. Variantes por área

Se recomienda utilizar una clase en el elemento `body`:

```html
<body class="area-home">
<body class="area-support">
<body class="area-staging">
<body class="area-common">
<body class="area-noturningback">
```

Esto permitirá introducir pequeñas diferencias sin duplicar toda la hoja de estilos:

```css
.area-staging {
  --area-accent: var(--color-staging);
}

.area-support {
  --area-accent: var(--color-support);
}
```

Las variantes deberían limitarse principalmente a:

* color de acento;
* mensajes de estado;
* navegación activa;
* detalles menores de presentación.

---

## 7. Primera clasificación de decisiones

### Comunes y obligatorias

* favicon;
* logotipo;
* tipografía;
* variables de color;
* anchura de contenido;
* estilos base de botones;
* estilos base de tarjetas;
* cabecera;
* pie;
* criterios de navegación;
* adaptación móvil;
* estados de foco y accesibilidad.

### Comunes con variantes

* color de acento;
* nombre del área;
* enlaces de navegación;
* aviso de uso interno;
* composición de la portada;
* densidad de las tarjetas.

### Propias de cada proyecto

* contenido;
* funciones;
* tablas;
* filtros;
* formularios;
* gráficos;
* mapas;
* fichas;
* scripts;
* navegación funcional interna.

---

## 8. Orden propuesto para la Fase 5

### Fase 5A — Inventario y criterios comunes

* revisar los estilos actuales;
* identificar duplicidades;
* fijar componentes comunes;
* acordar estructura de common.

### Fase 5B — Identidad base

* favicon;
* logo;
* paleta;
* tipografía;
* variables CSS;
* anchos y espaciados.

### Fase 5C — Cabecera, pie y navegación

* construir una versión común;
* aplicarla primero en home;
* validar escritorio y móvil;
* extender después a support y staging.

### Fase 5D — Componentes

* tarjetas;
* botones;
* avisos;
* etiquetas;
* bloques de presentación.

### Fase 5E — Aplicación progresiva

Orden recomendado:

1. home;
2. common;
3. support;
4. staging;
5. noturningback;
6. ajustes generales mínimos en Corrupción.

### Fase 5F — Verificación

* coherencia visual;
* enlaces;
* móvil;
* accesibilidad básica;
* ausencia de dependencias rotas;
* comprobación de que los proyectos mantienen su funcionalidad.

---

## 9. Resultado de la primera tarea

Se consideran elementos comunes del ecosistema:

* identidad gráfica;
* favicon y logotipo;
* paleta y variables;
* tipografía;
* cabecera;
* pie;
* navegación general;
* botones;
* tarjetas;
* contenedores;
* espaciados;
* adaptación móvil;
* estructura base de páginas y páginas de proyecto.

Se consideran elementos específicos:

* contenidos;
* funcionalidades;
* componentes de datos;
* navegación interna compleja;
* estilos directamente vinculados a la lógica de cada aplicación.

La siguiente actuación debe ser un inventario técnico de los CSS, cabeceras, pies, logotipos y favicons existentes, sin modificar todavía ninguna web.
