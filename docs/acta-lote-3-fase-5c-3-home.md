# Acta de salida - Lote 3 (Fase 5C.3 Home)

Fecha: 2026-07-12
Estado: completado
Resultado: limpieza por archivado (sin borrado definitivo)

## 1) Objetivo del lote

Reducir deuda tecnica local en Home moviendo activos no referenciados a una zona legacy, sin eliminarlos.

## 2) Cambios aplicados

Se creo:

- C:/jumalenin-ecosistema/sites/home/assets/_legacy/
- C:/jumalenin-ecosistema/sites/home/assets/_legacy/css/
- C:/jumalenin-ecosistema/sites/home/assets/_legacy/img/
- C:/jumalenin-ecosistema/sites/home/assets/_legacy/README.md

Se movio a legacy:

- assets/css/common-core.css -> assets/_legacy/css/common-core.css
- assets/css/home.css -> assets/_legacy/css/home.css
- assets/css/site.css -> assets/_legacy/css/site.css
- assets/img/logo-jumalenin.svg.png -> assets/_legacy/img/logo-jumalenin.svg.png

## 3) Evidencia tecnica

- Busqueda de referencias previa: sin referencias activas a esos activos en Home.
- Estado resultante:
  - `assets/css` vacio
  - `assets/img` conserva solo `favicon.svg`
- Home sigue respondiendo en runtime (verificacion de disponibilidad de pagina principal).

## 4) Estado git observado en Home

- `D assets/css/common-core.css`
- `D assets/css/home.css`
- `D assets/css/site.css`
- `D assets/img/logo-jumalenin.svg.png`
- `M index.html`
- `?? assets/_legacy/`

Nota: `M index.html` proviene del Lote 2.

## 5) Checklist del lote

- [x] candidatos sin referencia activa detectada
- [x] movimiento a `_legacy` completado
- [x] sin borrado irreversible
- [x] Home operativo

## 6) Rollback del lote

Restauracion completa con git (repo Home):

- `git -C C:/jumalenin-ecosistema/sites/home restore -- .`

Restauracion selectiva de este lote:

- `git -C C:/jumalenin-ecosistema/sites/home restore -- assets/css/common-core.css assets/css/home.css assets/css/site.css assets/img/logo-jumalenin.svg.png`
- eliminar luego `assets/_legacy` si se revierte completamente

## 7) Decision de puerta (GO / NO-GO)

Decision: GO para Lote 4 (cierre tecnico final de 5C.3).
