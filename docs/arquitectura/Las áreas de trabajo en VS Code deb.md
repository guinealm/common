Las **áreas de trabajo en VS Code** deberían coincidir, casi exactamente, con los **repositorios/proyectos GitHub**, no con el dominio completo. Es decir: abrirías en VS Code **un proyecto cada vez**, salvo casos especiales.

Según la estructura del anexo —`jumalenin.com`, `clima`, `noturningback`, `support` y `staging`— yo definiría estas áreas de trabajo. 

# Áreas de trabajo recomendadas

```text id="2m966h"
VS Code
│
├── 1. jumalenin-home
├── 2. NHMA-beta
├── 3. noturningback
├── 4. jumalenin-support
├── 5. jumalenin-staging
└── 6. jumalenin-common
```

## 1. Área de trabajo: `jumalenin-home`

Para el dominio principal:

```text id="y9sg7u"
jumalenin.com
```

Carpeta local:

```text id="mehz95"
C:\Users\...\Proyectos\jumalenin-home
```

Repositorio GitHub:

```text id="2i2rji"
guinealm/jumalenin-home
```

Uso:

* página de entrada;
* enlaces a los subdominios;
* presentación general del ecosistema Jumalenin.

Estructura:

```text id="db9i2k"
jumalenin-home/
│
├── index.html
├── README.md
├── AGENTS.md
└── assets/
    ├── css/
    ├── img/
    └── js/
```

Esta área sería pequeña y estable.

---

## 2. Área de trabajo: `NHMA-beta`

Para:

```text id="mz2dm5"
clima.jumalenin.com
```

Carpeta local:

```text id="x0gqvw"
C:\Users\...\Proyectos\NHMA-beta
```

Repositorio GitHub:

```text id="q14go1"
guinealm/NHMA
```

o, si decides renombrarlo:

```text id="a4es41"
guinealm/NHMA-beta
```

Uso:

* desarrollo actual de la web climática;
* pruebas;
* versión beta;
* cambios frecuentes;
* páginas en construcción.

Estructura:

```text id="wj263y"
NHMA-beta/
│
├── index.html
├── pagina1.html
├── pagina11.html
├── pagina12.html
├── pagina13.html
├── ...
├── assets/
│   ├── css/
│   ├── img/
│   ├── js/
│   └── data/
├── docs/
├── README.md
└── AGENTS.md
```

Esta sería una de tus áreas de trabajo principales.

---

## 3. Área de trabajo: `noturningback`

Para:

```text id="4koqpt"
noturningback.jumalenin.com
```

Carpeta local:

```text id="dvznb6"
C:\Users\...\Proyectos\noturningback
```

Repositorio GitHub:

```text id="0grpn6"
guinealm/noturningback
```

Uso:

* versión definitiva de NHMA;
* código limpio;
* estructura más estable;
* menos experimentos.

Estructura sugerida:

```text id="vpxgfe"
noturningback/
│
├── index.html
├── pages/
│   ├── 01-esta-cambiando.html
│   ├── 02-hace-dano.html
│   ├── 03-por-que.html
│   ├── 04-que-debe-hacer-el-mundo.html
│   ├── 05-que-puedo-hacer-yo.html
│   └── 06-como-nos-enganan.html
├── assets/
│   ├── css/
│   ├── img/
│   ├── js/
│   └── data/
├── docs/
├── README.md
└── AGENTS.md
```

Aquí no trabajaría directamente hasta que tengas clara la migración desde la beta.

---

## 4. Área de trabajo: `jumalenin-support`

Para:

```text id="4eezhg"
support.jumalenin.com
```

Carpeta local:

```text id="gwrgq2"
C:\Users\...\Proyectos\jumalenin-support
```

Repositorio GitHub:

```text id="dkitmz"
guinealm/jumalenin-support
```

Uso:

* proyectos públicos;
* temas que quieres compartir;
* páginas para hablar con otras personas;
* material divulgativo o técnico no climático.

Estructura:

```text id="vfdb6d"
jumalenin-support/
│
├── index.html
├── projects/
│   ├── energia/
│   │   ├── index.html
│   │   ├── assets/
│   │   └── docs/
│   ├── salud/
│   │   ├── index.html
│   │   ├── assets/
│   │   └── docs/
│   └── otro-tema/
├── assets/
│   ├── css/
│   ├── img/
│   ├── js/
│   └── data/
├── docs/
├── README.md
└── AGENTS.md
```

Esta también puede ser un área importante, porque puede agrupar varios temas.

---

## 5. Área de trabajo: `jumalenin-staging`

Para:

```text id="fi0v4z"
staging.jumalenin.com
```

Carpeta local:

```text id="oxw53o"
C:\Users\...\Proyectos\jumalenin-staging
```

Repositorio GitHub:

```text id="7u30s6"
guinealm/jumalenin-staging
```

Uso:

* temas privados;
* temas semiprivados;
* páginas con acceso restringido;
* pruebas no públicas.

Estructura:

```text id="6v8amj"
jumalenin-staging/
│
├── index.html
├── private/
│   └── tema-actual/
│       ├── index.html
│       ├── assets/
│       └── docs/
├── assets/
│   ├── css/
│   ├── img/
│   ├── js/
│   └── data/
├── docs/
├── README.md
└── AGENTS.md
```

Aquí tendría cuidado con GitHub: si el repositorio contiene información privada, debería ser **privado**.

---

## 6. Área de trabajo: `jumalenin-common`

Esta no corresponde a un subdominio. Es tu biblioteca común.

Carpeta local:

```text id="xvz90q"
C:\Users\...\Proyectos\jumalenin-common
```

Repositorio GitHub:

```text id="56fi32"
guinealm/jumalenin-common
```

Uso:

* CSS común;
* plantillas HTML;
* iconos;
* instrucciones para Codex;
* componentes reutilizables.

Estructura:

```text id="4v4zzx"
jumalenin-common/
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
├── templates/
│   ├── base.html
│   ├── landing.html
│   ├── articulo.html
│   ├── indice-proyectos.html
│   └── ficha-proyecto.html
│
├── img/
│   ├── logo-jumalenin.svg
│   └── icons/
│
├── docs/
│   ├── convenciones-html.md
│   ├── convenciones-css.md
│   └── como-usar-plantillas.md
│
├── README.md
└── AGENTS.md
```

Esta área no se despliega directamente. Sirve para copiar elementos a los demás proyectos.

# Cuándo abrir cada área de trabajo

| Quiero trabajar en...                 | Abro en VS Code     |
| ------------------------------------- | ------------------- |
| La portada general de Jumalenin       | `jumalenin-home`    |
| La web climática actual               | `NHMA-beta`         |
| La versión definitiva de NHMA         | `noturningback`     |
| Temas públicos compartibles           | `jumalenin-support` |
| Temas privados o semiprivados         | `jumalenin-staging` |
| CSS, plantillas o componentes comunes | `jumalenin-common`  |

# Lo que no haría

No abriría todo esto como una sola área gigante:

```text id="508i2r"
jumalenin-ecosistema/
  jumalenin-home/
  NHMA-beta/
  noturningback/
  support/
  staging/
  common/
```

Técnicamente se puede, pero para ti complica:

* Git;
* Codex;
* despliegues;
* control de cambios;
* riesgo de tocar archivos equivocados;
* claridad mental.

Mejor: **un proyecto = una carpeta = un repositorio = un área de trabajo VS Code**.

# Excepción: área multi-root de VS Code

VS Code permite áreas de trabajo con varias carpetas. Podrías tener una llamada:

```text id="wj29l1"
jumalenin.code-workspace
```

con:

```text id="1dzyv9"
NHMA-beta
jumalenin-common
```

Esto sería útil si estás copiando CSS común a NHMA.

Pero no lo usaría como forma normal de trabajo. Solo para momentos puntuales.

Ejemplo de uso puntual:

```text id="umm1pf"
Área multi-root temporal:
- NHMA-beta
- jumalenin-common
```

Así puedes ver ambos árboles de archivos a la vez.

# Recomendación operativa

Tu rutina debería ser:

```text id="55meht"
1. Abrir VS Code
2. Archivo → Abrir carpeta
3. Elegir un solo proyecto:
   - NHMA-beta
   - jumalenin-support
   - etc.
4. Trabajar con Codex dentro de esa carpeta
5. Revisar cambios en Source Control
6. Probar con Live Server
7. Commit
8. Sync / Push
```

# Organización local sugerida

En tu PC:

```text id="yayftu"
C:\Users\Luis\Documents\ProyectosWeb\
│
├── jumalenin-home\
├── NHMA-beta\
├── noturningback\
├── jumalenin-support\
├── jumalenin-staging\
└── jumalenin-common\
```

O más corto:

```text id="5gq1h0"
C:\Users\Luis\Web\
│
├── jumalenin-home\
├── NHMA-beta\
├── noturningback\
├── jumalenin-support\
├── jumalenin-staging\
└── jumalenin-common\
```

# Mi recomendación final

Crearía **seis áreas de trabajo VS Code**:

```text id="de41yi"
1. jumalenin-home
2. NHMA-beta
3. noturningback
4. jumalenin-support
5. jumalenin-staging
6. jumalenin-common
```

Y trabajaría casi siempre con una sola abierta. Para tu caso, las más usadas serían:

```text id="vgrh22"
NHMA-beta
jumalenin-support
jumalenin-common
```

`noturningback` la dejaría preparada, pero no la usaría intensamente hasta que decidas migrar la beta a versión definitiva.
