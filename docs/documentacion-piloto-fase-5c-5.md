# Fase 5C.5 - Documentacion del piloto

Fecha de cierre: 2026-07-12
Estado: completado
Piloto: migracion controlada de Home al contrato del nucleo comun (Common)

## 1) Resumen ejecutivo

Se ejecuto un piloto tecnico por lotes sobre Home para validar el modelo de arquitectura definido en 5C.2.

Resultado global:

- exito tecnico en local y en repositorio
- despliegue realizado en hosting
- verificacion funcional positiva en web publica

Commit de referencia del piloto en Home:

- `9595365` (`fase5c3-home-semantic-legacy`)

## 2) Alcance del piloto

Incluido:

- verificacion de contrato CSS canonico desde Common
- alineacion semantica de `header/nav/footer` en Home
- archivado de activos locales sin uso en `assets/_legacy`
- validacion y actas por lote

Excluido:

- cambios estructurales en Common no relacionados al contrato
- cambios DNS
- intervenciones en otros sitios fuera de Home

## 3) Evidencia documental generada

- [docs/arquitectura-tecnica-fase-5c-1.md](docs/arquitectura-tecnica-fase-5c-1.md)
- [docs/arquitectura-definitiva-nucleo-comun-fase-5c-2.md](docs/arquitectura-definitiva-nucleo-comun-fase-5c-2.md)
- [docs/plan-ejecucion-fase-5c-3-home.md](docs/plan-ejecucion-fase-5c-3-home.md)
- [docs/acta-lote-0-fase-5c-3-home.md](docs/acta-lote-0-fase-5c-3-home.md)
- [docs/acta-lote-1-fase-5c-3-home.md](docs/acta-lote-1-fase-5c-3-home.md)
- [docs/acta-lote-2-fase-5c-3-home.md](docs/acta-lote-2-fase-5c-3-home.md)
- [docs/acta-lote-3-fase-5c-3-home.md](docs/acta-lote-3-fase-5c-3-home.md)
- [docs/acta-lote-4-fase-5c-3-home.md](docs/acta-lote-4-fase-5c-3-home.md)
- [docs/hoja-ejecucion-despliegue-home-post-5c3.md](docs/hoja-ejecucion-despliegue-home-post-5c3.md)

## 4) Cambios tecnicos aplicados

Archivo principal actualizado:

- `sites/home/index.html`

Cambios funcionales del lote semantico:

- `body` con clase `site-shell`
- `header` alineado con clases de layout comun
- `nav` semantico explicito (Clima, Support, Staging)
- `main` y `footer` alineados al contrato comun
- enlace de pie a Common

Activos archivados (sin borrado irreversible):

- `sites/home/assets/_legacy/css/common-core.css`
- `sites/home/assets/_legacy/css/home.css`
- `sites/home/assets/_legacy/css/site.css`
- `sites/home/assets/_legacy/img/logo-jumalenin.svg.png`
- `sites/home/assets/_legacy/README.md`

## 5) Validaciones realizadas

Validaciones de contrato:

- orden CSS canonico correcto: core -> layout -> components
- favicon canonico de Common
- ausencia de CSS local activo en `index.html`

Validaciones tecnicas:

- HTML sin errores reportados en `index.html`
- estado Git consistente por lote
- rollback definido por lote y global

Validaciones funcionales en web:

- Home operativo tras deploy
- enlaces de Clima y Support operativos
- enlace de Staging operativo con control de acceso (401 esperado)
- enlace "Nucleo visual comun" operativo
- recursos canonicos de Common accesibles

## 6) Incidencias y aclaraciones

1. `staging.jumalenin.com` devuelve 401:
   - no se considera fallo del piloto; corresponde a proteccion del entorno.

2. Diferencias temporales entre estado local y web publica:
   - se detectaron durante la fase de despliegue y se resolvieron tras publicar en hosting.

3. Verificacion de cache:
   - se recomienda siempre recarga forzada o ventana privada para confirmacion final.

4. Verificacion movil en rotacion:
   - si el telefono no gira, revisar bloqueo de orientacion del sistema antes de validar landscape.

## 7) Criterios de exito (resultado)

Criterios cumplidos:

- arquitectura 5C.2 aplicada en Home
- deuda local reducida mediante archivado controlado
- trazabilidad completa por actas y commit
- despliegue final confirmado por usuario en hosting

Decision final del piloto:

- aprobado

## 8) Lecciones aprendidas

1. El enfoque por lotes reduce riesgo y acelera rollback.
2. Documentar evidencia por lote evita ambiguedad al desplegar.
3. Mantener assets legacy archivados antes de borrar es una practica segura.
4. Validar siempre entorno protegido (401) como estado esperado, no como error.

## 9) Recomendacion post-piloto

1. Reutilizar la misma metodologia por lotes en siguientes sitios.
2. Mantener una unica fuente de verdad visual en Common.
3. Programar una fase posterior de depuracion definitiva de legacy, ya con ventana controlada.
