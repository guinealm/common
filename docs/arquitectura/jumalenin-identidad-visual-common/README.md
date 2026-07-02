# Jumalenin - identidad visual común

Este paquete sustituye la versión anterior basada en `home/assets`.

## Arquitectura decidida

- `common` almacena la identidad visual común.
- `home` solo consume esa identidad.
- `clima`, `support`, `staging` y futuros proyectos también deberán consumir `common`.

## Estructura

```text
common/
  index.html
  assets/
    css/
      jumalenin-core.css
      jumalenin-layout.css
      jumalenin-components.css
    img/
      favicon.svg
      logo.svg
      logo-horizontal.svg

home/
  index.html
```

## Publicación recomendada

`common/` debe publicarse como:

```text
https://common.jumalenin.com
```

`home/index.html` carga los CSS y SVG desde:

```text
https://common.jumalenin.com/assets/...
```

## Orden recomendado

1. Publicar primero `common`.
2. Comprobar `https://common.jumalenin.com`.
3. Publicar después `home`.
4. Comprobar que `home` carga CSS, logo y favicon desde `common`.
