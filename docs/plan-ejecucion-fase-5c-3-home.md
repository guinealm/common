# Fase 5C.3 - Plan de ejecucion tecnico por lotes (Home)

Fecha: 2026-07-12  
Estado: plan previo. No se aplican cambios en esta fase.

## 1. Objetivo

Aplicar en Home la arquitectura definida en 5C.2 de forma controlada, en lotes pequenos, con validaciones y rollback por cada lote.

Alcance de ejecucion futura:

- sitio Home en `C:/jumalenin-ecosistema/sites/home`
- consumo de nucleo comun desde `https://common.jumalenin.com/assets/...`
- limpieza de activos locales no usados (solo cuando se confirme)

Fuera de alcance en este plan:

- cambios en Common
- cambios DNS
- cambios en otros subdominios

## 2. Principios de ejecucion

1. Un lote = una intencion tecnica clara.
2. No avanzar al siguiente lote sin pasar validaciones del lote actual.
3. Cada lote debe tener rollback rapido y probado.
4. Evitar cambios cosmeticos no relacionados.
5. Mantener deploy estable en todo momento.

## 3. Lotes propuestos

### Lote 0 - Preflight y linea base

Objetivo:

- congelar estado inicial y evidencia tecnica antes de tocar archivos.

Acciones:

1. Confirmar arbol de Home.
2. Capturar referencias actuales en `index.html` (CSS, favicon, enlaces).
3. Guardar snapshot de estado de git en repo Home.
4. Guardar checklist de smoke test inicial.

Checklist:

- [ ] Existe `sites/home/index.html`
- [ ] `index.html` carga 3 CSS de Common
- [ ] favicon apunta a Common
- [ ] Home abre y renderiza tarjetas

Validaciones:

- `git -C C:/jumalenin-ecosistema/sites/home status --short`
- `git -C C:/jumalenin-ecosistema/sites/home rev-parse --short HEAD`
- verificacion visual Home en navegador

Rollback:

- no aplica (sin cambios)

Puerta de salida:

- evidencia inicial guardada y estado limpio/comprendido

---

### Lote 1 - Normalizacion de contrato HTML de Home

Objetivo:

- dejar Home alineado con contrato 5C.2 sin introducir estilos locales nuevos.

Acciones previstas:

1. Revisar y fijar bloque `<head>` de Home con este orden:
   - `jumalenin-core.css`
   - `jumalenin-layout.css`
   - `jumalenin-components.css`
2. Mantener favicon canonico de Common.
3. No agregar CSS local en este lote.

Checklist:

- [ ] Orden CSS canonico correcto
- [ ] Sin duplicidad de `<link rel="stylesheet">`
- [ ] favicon unico y canonico

Validaciones:

- inspeccion de fuente HTML final
- carga HTTP 200 de los tres CSS
- smoke visual desktop y movil

Rollback:

- `git -C C:/jumalenin-ecosistema/sites/home restore -- index.html`

Puerta de salida:

- Home visualmente igual o mejor, sin regresiones

---

### Lote 2 - Semantica de estructura (header/nav/footer)

Objetivo:

- alinear estructura de Home al contrato semantico del nucleo comun.

Acciones previstas:

1. Mantener `header` y `footer` existentes si son validos.
2. Decidir si se incorpora `nav` semantico explicito o se mantiene navegacion por tarjetas.
3. Si se anaden clases de layout comun, hacerlo sin romper contenido.

Checklist:

- [ ] Header semantico presente
- [ ] Navegacion definida (explicita o por tarjetas, documentada)
- [ ] Footer semantico presente

Validaciones:

- auditoria HTML basica
- test de foco teclado en enlaces principales
- smoke visual en anchos: 360, 768, 1280

Rollback:

- `git -C C:/jumalenin-ecosistema/sites/home restore -- index.html`

Puerta de salida:

- semantica coherente y sin perdida de accesibilidad basica

---

### Lote 3 - Limpieza de activos locales no usados

Objetivo:

- reducir deuda tecnica local en Home sin afectar runtime.

Candidatos detectados en 5C.1:

- `assets/css/home.css`
- `assets/css/common-core.css` (vacio)
- `assets/css/site.css` (vacio)
- `assets/img/logo-jumalenin.svg.png`

Acciones previstas:

1. Verificar referencias reales de cada candidato.
2. Mover candidatos a carpeta de archivo interno (no borrado directo en primer pase), por ejemplo `assets/_legacy/`.
3. Confirmar que `index.html` no depende de ellos.

Checklist:

- [ ] 0 referencias activas a candidatos
- [ ] activos movidos a `_legacy` (no eliminados)
- [ ] Home sin cambios visuales

Validaciones:

- busqueda global de referencias
- smoke visual completo
- comprobacion de consola sin 404 nuevos

Rollback:

- restaurar movimiento con git:
  - `git -C C:/jumalenin-ecosistema/sites/home restore --source=HEAD --staged --worktree .`
  - o `git -C C:/jumalenin-ecosistema/sites/home restore -- .`

Puerta de salida:

- deuda local reducida y cero impacto funcional

---

### Lote 4 - Cierre tecnico y trazabilidad

Objetivo:

- cerrar la fase con evidencia y lista de decisiones finales.

Acciones:

1. Ejecutar checklist final de regresion.
2. Documentar cambios aplicados y cambios no aplicados.
3. Preparar commit(s) por lote o commit unico segun politica.

Checklist:

- [ ] Home carga CSS canonicamente desde Common
- [ ] favicon canonico activo
- [ ] sin activos locales innecesarios en uso
- [ ] sin errores funcionales visibles

Validaciones:

- prueba rapida de enlaces principales
- prueba en movil y desktop
- revision de `git diff` enfocada en alcance

Rollback:

- rollback por lote (preferido)
- rollback total:
  - `git -C C:/jumalenin-ecosistema/sites/home restore -- .`

Puerta de salida:

- fase 5C.3 completada y lista para 5C.4 (si aplica)

## 4. Matriz de riesgos y mitigacion

1. Riesgo: ruptura visual por orden CSS
   - Mitigacion: validar orden exacto en Lote 1 y smoke visual inmediato.

2. Riesgo: eliminar activo aparentemente no usado pero requerido por futuro
   - Mitigacion: mover a `_legacy` antes de borrar definitivo.

3. Riesgo: cambios excesivos en un solo paso
   - Mitigacion: lotes pequenos + puerta de salida por lote.

4. Riesgo: rollback incompleto
   - Mitigacion: comandos de rollback definidos por lote y prueba de rollback rapida.

## 5. Plan de validacion minima (smoke test)

Casos minimos:

1. Carga de `home.jumalenin.com` sin errores visibles.
2. Render de header, tarjetas y footer.
3. Apertura de enlaces de tarjetas (Clima, Support, Staging).
4. Carga correcta de favicon.
5. Sin 404 nuevos en consola para CSS/imagenes.

## 6. Criterio de GO / NO-GO por lote

GO:

- checklist del lote al 100%
- sin regresion visible
- rollback confirmado disponible

NO-GO:

- cualquier regresion visual importante
- dudas sobre activos no usados
- inconsistencias de rutas sin resolver

## 7. Resultado esperado al finalizar 5C.3

- Home alineado con el contrato del nucleo comun
- rutas y dependencias CSS estables
- deuda tecnica local reducida y trazable
- base lista para evolucion de Home sin romper Common
