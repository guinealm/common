Según el anexo, la arquitectura prevista es:



\* `jumalenin.com`: home del dominio, con acceso a los 4 subdominios.

\* `clima.jumalenin.com`: NHMA versión beta.

\* `noturningback.jumalenin.com`: NHMA definitiva, aún sin empezar.

\* `support.jumalenin.com`: temas públicos.

\* `staging.jumalenin.com`: temas privados o semiprivados, con acceso restringido. 



Yo lo definiría así.



\# 1. Estructura general recomendada



Separaría \*\*dominio\*\*, \*\*subdominios\*\*, \*\*código común\*\* y \*\*proyectos\*\*.



```text

jumalenin-ecosistema/

│

├── README.md

├── docs/

│   ├── arquitectura.md

│   ├── convenciones.md

│   └── despliegue-hostinger.md

│

├── common/

│   ├── css/

│   │   ├── common-core.css

│   │   ├── common-nav-footer.css

│   │   └── common-components.css

│   ├── js/

│   │   └── common-ui.js

│   ├── img/

│   │   ├── logo-jumalenin.svg

│   │   └── icons/

│   └── templates/

│       ├── page-base.html

│       ├── page-listado.html

│       └── page-articulo.html

│

├── sites/

│   ├── home/

│   ├── clima-beta/

│   ├── noturningback/

│   ├── support/

│   └── staging/

│

└── AGENTS.md

```



Pero para GitHub y despliegue real, no lo haría necesariamente como un único repositorio. Haría \*\*repositorios separados\*\*, con una carpeta común de plantillas.



\# 2. Repositorios GitHub



\## Opción recomendada: varios repositorios



```text

GitHub / guinealm

│

├── jumalenin-home

├── NHMA-beta

├── noturningback

├── jumalenin-support

├── jumalenin-staging

└── jumalenin-common

```



Esta es la opción más limpia.



| Repositorio         | Subdominio                    | Función                              |

| ------------------- | ----------------------------- | ------------------------------------ |

| `jumalenin-home`    | `jumalenin.com`               | Página de entrada al ecosistema      |

| `NHMA-beta`         | `clima.jumalenin.com`         | Versión beta de la web climática     |

| `noturningback`     | `noturningback.jumalenin.com` | Versión definitiva de NHMA           |

| `jumalenin-support` | `support.jumalenin.com`       | Proyectos públicos compartibles      |

| `jumalenin-staging` | `staging.jumalenin.com`       | Proyectos privados o semiprivados    |

| `jumalenin-common`  | sin dominio directo           | CSS, plantillas, componentes comunes |



Ventaja: cada web puede evolucionar sin romper las demás.



Inconveniente: los elementos comunes no se actualizan automáticamente en todos los sitios. Pero para tu caso eso es una ventaja: evita que un cambio de CSS rompa varias webs a la vez.



\# 3. Estructura de cada proyecto web



Cada repositorio web debería tener una estructura parecida:



```text

nombre-proyecto/

│

├── index.html

├── README.md

├── AGENTS.md

│

├── assets/

│   ├── css/

│   │   ├── common-core.css

│   │   ├── common-nav-footer.css

│   │   ├── common-components.css

│   │   └── site.css

│   │

│   ├── js/

│   │   ├── common-ui.js

│   │   └── site.js

│   │

│   ├── img/

│   │   ├── logo.svg

│   │   └── ...

│   │

│   └── data/

│       └── datos.json

│

├── pages/

│   ├── tema1.html

│   ├── tema2.html

│   └── tema3.html

│

└── docs/

&#x20;   ├── notas-funcionales.md

&#x20;   ├── cambios.md

&#x20;   └── pendientes.md

```



\## Significado



\* `index.html`: portada del subdominio.

\* `pages/`: páginas interiores.

\* `assets/css/`: estilos.

\* `assets/js/`: JavaScript.

\* `assets/data/`: JSON u otros datos.

\* `docs/`: documentación interna del proyecto.

\* `AGENTS.md`: instrucciones para Codex.

\* `README.md`: explicación del proyecto para humanos.



\# 4. Estructura de `jumalenin.com`



El dominio principal no debería tener mucho contenido. Sería una \*\*home lanzadera\*\*.



```text

jumalenin-home/

│

├── index.html

├── README.md

├── AGENTS.md

│

└── assets/

&#x20;   ├── css/

&#x20;   │   ├── common-core.css

&#x20;   │   └── site.css

&#x20;   └── img/

&#x20;       └── logo-jumalenin.svg

```



Contenido de la home:



```text

Jumalenin

│

├── Clima / NHMA Beta

├── No Turning Back / NHMA definitiva

├── Support / Proyectos públicos

└── Staging / Proyectos privados

```



Visualmente debería ser muy simple: cuatro tarjetas grandes.



\# 5. Estructura de `clima.jumalenin.com`



Este es tu proyecto NHMA actual, versión beta.



```text

NHMA-beta/

│

├── index.html

├── pagina1.html

├── pagina11.html

├── pagina12.html

├── pagina13.html

├── pagina14.html

├── pagina16.html

├── pagina2.html

├── pagina21.html

├── ...

│

├── assets/

│   ├── css/

│   │   ├── common-core.css

│   │   ├── common-nav-footer.css

│   │   ├── pages.css

│   │   └── nhma-beta.css

│   ├── js/

│   ├── img/

│   └── data/

│

└── docs/

&#x20;   ├── estructura-nhma.md

&#x20;   ├── fuentes.md

&#x20;   ├── pendientes-beta.md

&#x20;   └── criterios-graficos.md

```



Aquí mantendría la estructura que ya tienes, porque es una web trabajada.



\# 6. Estructura de `noturningback.jumalenin.com`



Esta sería la versión definitiva. No conviene empezar copiando todo sin criterio. La usaría como \*\*versión limpia\*\* de NHMA.



```text

noturningback/

│

├── index.html

├── README.md

├── AGENTS.md

│

├── assets/

│   ├── css/

│   │   ├── common-core.css

│   │   ├── common-nav-footer.css

│   │   ├── common-components.css

│   │   └── noturningback.css

│   ├── js/

│   ├── img/

│   └── data/

│

├── pages/

│   ├── 01-esta-cambiando.html

│   ├── 02-hace-dano.html

│   ├── 03-por-que.html

│   ├── 04-que-debe-hacer-el-mundo.html

│   ├── 05-que-puedo-hacer-yo.html

│   └── 06-como-nos-enganan.html

│

└── docs/

&#x20;   ├── plan-version-definitiva.md

&#x20;   ├── fuentes.md

&#x20;   ├── decisiones-editoriales.md

&#x20;   └── migracion-desde-beta.md

```



Aquí cambiaría nombres como `pagina11.html` por nombres más legibles:



```text

pagina11.html → 01-01-temperatura-global.html

pagina12.html → 01-02-temperatura-mar.html

pagina13.html → 01-03-nivel-mar.html

```



Pero solo en la versión definitiva, no necesariamente en la beta.



\# 7. Estructura de `support.jumalenin.com`



Este subdominio sería público, para temas que quieres compartir con otras personas.



```text

jumalenin-support/

│

├── index.html

├── README.md

├── AGENTS.md

│

├── assets/

│   ├── css/

│   ├── js/

│   ├── img/

│   └── data/

│

├── projects/

│   ├── energia/

│   │   ├── index.html

│   │   ├── assets/

│   │   └── docs/

│   │

│   ├── salud/

│   │   ├── index.html

│   │   ├── assets/

│   │   └── docs/

│   │

│   └── otro-tema/

│       ├── index.html

│       └── assets/

│

└── docs/

&#x20;   ├── indice-proyectos.md

&#x20;   └── criterios-publicacion.md

```



Ejemplo de URLs:



```text

support.jumalenin.com/energia/

support.jumalenin.com/salud/

support.jumalenin.com/otro-tema/

```



Este subdominio debería tener un menú de proyectos.



\# 8. Estructura de `staging.jumalenin.com`



Este es diferente: privado o semiprivado. No lo mezclaría con `support`.



```text

jumalenin-staging/

│

├── index.html

├── README.md

├── AGENTS.md

│

├── assets/

│   ├── css/

│   ├── js/

│   ├── img/

│   └── data/

│

├── private/

│   └── tema-actual/

│       ├── index.html

│       ├── assets/

│       └── docs/

│

└── docs/

&#x20;   ├── control-acceso.md

&#x20;   └── temas-privados.md

```



Aquí usaría acceso restringido desde Hostinger, por ejemplo:



\* protección por contraseña del directorio;

\* o restricción mediante panel de hosting;

\* o una página no enlazada públicamente, aunque esto no es seguridad real.



Para contenido realmente privado, mejor contraseña.



\# 9. Repositorio común `jumalenin-common`



Este sería muy útil para ti.



```text

jumalenin-common/

│

├── README.md

│

├── css/

│   ├── common-core.css

│   ├── common-nav-footer.css

│   ├── common-components.css

│   ├── common-cards.css

│   └── common-forms.css

│

├── js/

│   ├── common-ui.js

│   └── common-menu.js

│

├── img/

│   ├── logo-jumalenin.svg

│   ├── logo-nhma.svg

│   └── icons/

│

├── templates/

│   ├── base.html

│   ├── landing.html

│   ├── article.html

│   ├── project-index.html

│   └── data-page.html

│

└── docs/

&#x20;   ├── como-usar.md

&#x20;   ├── convenciones-css.md

&#x20;   └── convenciones-html.md

```



Pero no lo usaría como dependencia automática. Lo usaría como \*\*biblioteca de copia controlada\*\*.



Ejemplo:



```text

jumalenin-common/css/common-core.css

&#x20;       ↓ copiar

NHMA-beta/assets/css/common-core.css

&#x20;       ↓ copiar

jumalenin-support/assets/css/common-core.css

```



\# 10. Archivo `AGENTS.md` para Codex



Cada proyecto debería tener su propio `AGENTS.md`.



Ejemplo para todos tus proyectos:



```text

Este proyecto es una web HTML5, CSS3 y JavaScript básico, sin frameworks.



Reglas generales:

\- No usar React, Vue, Angular, Bootstrap ni Tailwind.

\- Mantener HTML semántico.

\- Separar estructura, presentación y comportamiento.

\- No modificar varios archivos sin explicar antes el plan.

\- Hacer cambios pequeños, reversibles y fáciles de revisar en Git.

\- Mantener compatibilidad con despliegue estático en Hostinger.

\- No cambiar nombres de archivos existentes sin justificarlo.

\- No eliminar contenido sin pedir confirmación.

\- Antes de modificar, revisar la estructura del proyecto.

\- Después de modificar, resumir archivos tocados y motivo.

```



Para NHMA añadiría:



```text

Reglas específicas NHMA:

\- Mantener tono divulgativo, sobrio y basado en fuentes científicas.

\- No inventar datos climáticos.

\- Mantener citas y enlaces a fuentes.

\- Preservar la estructura de navegación existente salvo instrucción contraria.

```



\# 11. Configuración GitHub



Para cada repositorio:



\## Ramas



Usaría algo simple:



```text

main

```



Y, solo cuando haga falta:



```text

beta

experimentos

```



No complicaría mucho más.



\## Commits



Usaría mensajes claros:



```text

Añade estructura inicial de support

Corrige menú principal

Actualiza CSS común

Crea página energía

Revisa responsive de portada

```



\## README mínimo



Cada repositorio debería tener un `README.md` con:



```text

\# Nombre del proyecto



\## Objetivo

Breve descripción.



\## URL

https://...



\## Estructura

\- index.html

\- assets/css

\- assets/js

\- assets/img

\- pages o projects



\## Despliegue

Hostinger / subdominio correspondiente.



\## Estado

Beta / activo / experimental / privado.

```



\# 12. Relación con Hostinger



La correspondencia sería:



```text

jumalenin.com                  → jumalenin-home

clima.jumalenin.com            → NHMA-beta

noturningback.jumalenin.com    → noturningback

support.jumalenin.com          → jumalenin-support

staging.jumalenin.com          → jumalenin-staging

```



En Hostinger, cada subdominio debería apuntar a su propia carpeta:



```text

public\_html/

│

├── index.html                         ← jumalenin.com

│

├── clima/

│   └── index.html                     ← clima.jumalenin.com

│

├── noturningback/

│   └── index.html                     ← noturningback.jumalenin.com

│

├── support/

│   └── index.html                     ← support.jumalenin.com

│

└── staging/

&#x20;   └── index.html                     ← staging.jumalenin.com

```



\# 13. Criterio importante: no mezclar Beta y definitiva



Mantendría:



\* `clima.jumalenin.com`: sitio de trabajo, pruebas, beta.

\* `noturningback.jumalenin.com`: sitio limpio, estable, definitivo.



Cuando una página de beta esté madura, se migra a definitiva.



No haría que ambos apunten al mismo código.



\# 14. Mi recomendación final



La arquitectura que te propongo es:



```text

GitHub:

\- jumalenin-home

\- NHMA-beta

\- noturningback

\- jumalenin-support

\- jumalenin-staging

\- jumalenin-common

```



Con este uso:



```text

ChatGPT

&#x20; → define estructura, contenido, criterios y prompts



VS Code + Codex

&#x20; → aplica cambios técnicos en cada repositorio



GitHub

&#x20; → controla versiones



Hostinger

&#x20; → publica cada repositorio/subdominio



jumalenin-common

&#x20; → biblioteca común de CSS, plantillas e instrucciones

```



Para tu caso, esta estructura es suficientemente profesional, pero no excesivamente compleja. Mantiene separados los proyectos, permite reutilizar estilos y deja claro qué es público, qué es beta, qué es definitivo y qué es privado.



