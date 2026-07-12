# Acta de salida - Lote 4 (Fase 5C.3 Home)

Fecha: 2026-07-12
Estado: completado
Resultado: cierre tecnico de fase 5C.3 listo

## 1) Objetivo del lote

Cerrar 5C.3 con validaciones finales, estado de cambios y criterio de salida.

## 2) Validaciones finales

Validacion de archivo principal:

- `sites/home/index.html` sin errores reportados.

Validacion de disponibilidad externa:

- Home responde en URL publica.
- Recursos canonicos de Common (3 CSS + favicon) responden.

Validacion de estado git de Home:

- `M index.html` (Lote 2)
- `D assets/css/common-core.css` (movido a legacy en Lote 3)
- `D assets/css/home.css` (movido a legacy en Lote 3)
- `D assets/css/site.css` (movido a legacy en Lote 3)
- `D assets/img/logo-jumalenin.svg.png` (movido a legacy en Lote 3)
- `?? assets/_legacy/` (nuevo contenido de archivado)

## 3) Resultado consolidado de 5C.3

Lotes cerrados:

- Lote 0: baseline y evidencia inicial
- Lote 1: contrato HTML/CSS confirmado (sin cambios)
- Lote 2: semantica header/nav/footer alineada con nucleo comun
- Lote 3: limpieza de activos locales por archivado en `_legacy`
- Lote 4: validacion final y cierre

## 4) Nota operativa de despliegue

La verificacion por URL publica refleja el estado desplegado, no necesariamente el estado local inmediato del repositorio Home.

Para ver los cambios de Lote 2 y 3 en produccion, se requiere el flujo habitual de despliegue del sitio Home.

## 5) Rollback global de 5C.3

Rollback completo (repo Home):

- `git -C C:/jumalenin-ecosistema/sites/home restore -- .`

Rollback selectivo por lotes:

- Lote 2: `git -C C:/jumalenin-ecosistema/sites/home restore -- index.html`
- Lote 3: restaurar archivos movidos y eliminar `_legacy` si procede

## 6) Decision final de fase

Decision: 5C.3 COMPLETADA (tecnica local).

Siguiente fase sugerida:

- preparar paquete de despliegue y verificacion post-deploy para Home.
