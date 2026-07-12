# Acta de salida - Lote 0 (Fase 5C.3 Home)

Fecha: 2026-07-12
Estado: completado
Tipo: baseline tecnico sin cambios funcionales

## 1) Evidencia de linea base

Ruta verificada de Home:

- C:/jumalenin-ecosistema/sites/home

Archivos principales detectados:

- .git/
- assets/
- index.html
- README.md

Contrato actual en head de `index.html`:

- favicon: https://common.jumalenin.com/assets/img/favicon.svg
- CSS 1: https://common.jumalenin.com/assets/css/jumalenin-core.css
- CSS 2: https://common.jumalenin.com/assets/css/jumalenin-layout.css
- CSS 3: https://common.jumalenin.com/assets/css/jumalenin-components.css

## 2) Baseline de git (repo Home)

- Branch: main
- Commit corto: 3c427ea
- Estado corto: sin cambios reportados en salida (`git status --short` vacio)

## 3) Smoke tecnico inicial

### Home

- https://home.jumalenin.com/ responde y muestra contenido esperado (header, tarjetas, footer).

### Recursos criticos de Common usados por Home

- https://common.jumalenin.com/assets/css/jumalenin-core.css responde
- https://common.jumalenin.com/assets/css/jumalenin-layout.css responde
- https://common.jumalenin.com/assets/css/jumalenin-components.css responde
- https://common.jumalenin.com/assets/img/favicon.svg responde

### Destinos enlazados desde Home

- https://clima.jumalenin.com/ responde
- https://support.jumalenin.com/ responde
- https://staging.jumalenin.com/ devuelve 401 (acceso restringido), coherente con su naturaleza de entorno de pruebas privado

## 4) Checklist Lote 0

- [x] Existe `sites/home/index.html`
- [x] `index.html` carga 3 CSS de Common
- [x] favicon apunta a Common
- [x] Home abre y renderiza contenido esperado
- [x] Baseline git capturado (branch + commit + estado)

## 5) Riesgos observados en baseline

1. Dependencia total de Home respecto a disponibilidad de Common para CSS/favicon.
2. `staging` no es publico (401), por lo que no debe tratarse como fallo de Home.

## 6) Decision de puerta (GO / NO-GO)

Decision: GO para Lote 1.

Justificacion:

- baseline completo y consistente
- sin regresiones observadas
- contrato CSS actual ya coincide con el objetivo de 5C.2

## 7) Alcance del siguiente lote (Lote 1)

- revisar y fijar contrato HTML/CSS de Home sin introducir overrides locales nuevos
- mantener favicon canonico de Common
- mantener comportamiento visual esperado
