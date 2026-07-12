# Hoja de ejecucion - Home post 5C.3

Fecha: 2026-07-12
Objetivo: desplegar cambios de 5C.3 en Home y validar en minutos.
Alcance: C:/jumalenin-ecosistema/sites/home

## 1) Pre-deploy (2-3 min)

Checklist:

- Confirmar rama y estado:
  - git -C C:/jumalenin-ecosistema/sites/home rev-parse --abbrev-ref HEAD
  - git -C C:/jumalenin-ecosistema/sites/home rev-parse --short HEAD
  - git -C C:/jumalenin-ecosistema/sites/home status --short

- Confirmar archivos cambiados esperados:
  - index.html (semantica header/nav/footer)
  - assets/_legacy/ (archivado)

- Guardar evidencia previa:
  - capturas de home.jumalenin.com (home completo y cabecera)

Decision GO:

- GO si solo hay cambios esperados de 5C.3.
- NO-GO si aparecen cambios no relacionados.

## 2) Deploy (2-5 min)

Opcion A - despliegue por Git (si tu hosting tira de repo):

1. Commit en repo Home:
   - git -C C:/jumalenin-ecosistema/sites/home add index.html assets/_legacy assets/css assets/img
   - git -C C:/jumalenin-ecosistema/sites/home commit -m "Fase 5C.3 Home: semantica comun y archivado de activos legacy"

2. Push:
   - git -C C:/jumalenin-ecosistema/sites/home push origin main

3. Ejecutar proceso de publicacion del hosting (si aplica).

Opcion B - despliegue por copia de archivos (si no hay pipeline Git):

1. Publicar index.html actualizado.
2. Publicar carpeta assets/_legacy.
3. Mantener estructura de assets/img con favicon.svg operativo.

## 3) Post-check (3-5 min)

Comprobaciones minimas:

- URL principal:
  - https://home.jumalenin.com/

- Recursos canonicos:
  - https://common.jumalenin.com/assets/css/jumalenin-core.css
  - https://common.jumalenin.com/assets/css/jumalenin-layout.css
  - https://common.jumalenin.com/assets/css/jumalenin-components.css
  - https://common.jumalenin.com/assets/img/favicon.svg

- Validaciones funcionales:
  - se ve cabecera con logo horizontal
  - se ve nav con Clima, Support y Staging
  - se ven tarjetas de proyectos
  - se ve pie con enlace a Common

- Validaciones de consola:
  - sin 404 nuevos para CSS/imagenes

Criterio de exito:

- Home carga correcto en desktop y movil
- sin errores visuales graves

## 4) Rollback (1-3 min)

Rollback rapido por Git:

1. Revertir cambios del commit de despliegue:
   - git -C C:/jumalenin-ecosistema/sites/home log --oneline -n 5
   - git -C C:/jumalenin-ecosistema/sites/home revert <commit_sha>
   - git -C C:/jumalenin-ecosistema/sites/home push origin main

Rollback local previo a commit (si aun no desplegaste):

- git -C C:/jumalenin-ecosistema/sites/home restore -- .

Rollback selectivo de Lote 2:

- git -C C:/jumalenin-ecosistema/sites/home restore -- index.html

Rollback selectivo de Lote 3:

- git -C C:/jumalenin-ecosistema/sites/home restore -- assets/css/common-core.css assets/css/home.css assets/css/site.css assets/img/logo-jumalenin.svg.png
- eliminar assets/_legacy si se revierte totalmente

## 5) Cierre

Si Post-check es correcto:

- marcar 5C.3 como desplegada
- registrar fecha y commit en acta de cierre operativa
