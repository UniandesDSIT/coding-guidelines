# Flujo de Trabajo Git/GitHub — Ramas Base y RC

## 🎯 Objetivo
- Mantener **producción estable** en `master`.
- Asegurar camino claro de **features → producción**.
- Roles claros y definidos.
- Establecer un manejo estándar de **conflictos** durante el rebase/merge.

---

## 🛠️ Ramas base
- **master** → Producción (estable, solo versiones certificadas con tag).
- **beta** → Rama candidata, consolidación de releases antes de producción.
- **staging** → QA, validación del equipo de testing.
- **develop** → Integración de features en desarrollo.

### Ramas de soporte
- **feature/AB#** → ramas por Historia de Usuario.
- **bugfix/** → correcciones detectadas en QA/RC.
- **hotfix/** → correcciones críticas en producción.

---

## 👩‍💻 Rol del Desarrollador
1. Crear rama desde `staging`:
  ```bash
  git fetch origin
  git checkout develop
  git pull
  git checkout -b feature/AB1234-nombre
  ```
2. Subir cambios:
  ```bash
  git add .
  git commit -m "feat(AB#1234): descripción"
  git push -u origin feature/AB1234-nombre
  ```
3. PR → develop:

    Una vez aceptado sera deber del dearrollador probar garantizando la calidad de su feature, realizando todos los ajustes que considere pertinentes. Siempre desde la rama feature, y nuevos PR hacia develop para garantizar la integracion con los desarrollos del resto del equipo.

4.	Una vez validado en entorno dev, PR → staging:

    Este PR saldra de la rama feature/ (original) por eso sera fundamental mantenerla actualizada 

## 👀 Rol del Revisor
1. Revisar estándares de código.
2. Aprobar PR con Squash & merge.
3. Verificar mensajes de commit claros (Y manejo de llineamientos AB#).

## 🧑‍💼 Rol del Admin
- Nivela ramas base una vez se promueven cambios a productivo
- Crea rama rc/1.0.0 a partir del nuevo staging al inicio del nuevo ciclo de tiempo, normalmente un nuevo sprint 
- Traslada commits con cherry-pick de commits relacionados a HU y/o BUG la ventaja es que al haber usado squash para llevarlo a staging, existira un commit por feature y/o los necesarios por cada BUG
- Una vez cerrada la rama candidata, promovera dicha rama a rama beta (esto por efecto de pipeline no permite dinamismo en la rama a desplegar)
- Promueve beta → master con tag de version
```bash
git checkout master
git merge --ff-only origin/beta
git tag -a v1.0.0 -m "Release 1.0.0"
git push origin master --tags
```

## ⚔️ Resolución de conflictos

### Vía A — Rama alterna (no reescribe tu feature) - Recomendada si no se domina el comando rebase

Úsalo si: no quieres tocar la historia de tu feature, trabajas en equipo sobre esa rama, o prefieres resolver conflictos una sola vez y dejar el resultado listo para PR a develop.

Idea: crear una rama “de integración” basada en develop, llevar tu feature ahí, resolver conflictos una vez, y abrir PR → develop desde esa rama alterna.
```bash

# 1) Crear rama de "integración-conflictos" desde develop
git fetch origin
git checkout develop
git pull origin develop
git checkout -b feature/AB1234-conflictos-develop

# 2) Traer tu feature haciendo merge (aquí aparecerán los conflictos)
git merge --no-ff feature/AB#1234-original-feature

# 3) Resolver conflictos
git status
git add <archivos_resueltos>
git commit # se crea el commit de merge explícito

# 4) Probar local: Que la resolucion de conflictos y la integridad del producto no se viera afectada, incluyendo el desarrollo propio de la feature

# 5) Publicar y crear PR -> develop
git push -u origin feature/AB1234-conflictos-develop
# Abre PR base: develop, compare: feature/AB1234-conflictos-develop
```

### Vía B — Rebase

Usalo si: tu rama feature/* es solo tuya (no compartida) y quieres mantener la historia impecable sin “merge commits”.

Objetivo: re-aplicar tus commits de feature encima de origin/develop, resolviendo conflictos sobre la marcha.

```bash
# 1) Traer lo último y pararte en tu feature
git fetch origin
git checkout feature/AB1234-nombre

# 2) Rebasear contra develop
git rebase origin/develop

# 3) Si hay conflictos:
#   - Edita los archivos con <<<<<<< ======= >>>>>>>
git status                              # ver archivos en conflicto
git diff --name-only --diff-filter=U    # listar solo los conflictivos
git add <archivo_resuelto>
git rebase --continue                   # seguir con el siguiente commit

# (si te equivocaste)
# git rebase --abort

# 4) Probar local: build/tests

# 5) Publicar (reescribiste historia → usa push seguro)
git push --force-with-lease
```

### Recomendaciones prácticas

El modo visual a veces permite analizar los cambios y resolucion de conflictos con gran facilidad, y reduciendo errores. Por lo cual me permito realizar las siguientes recomendaciones

```bash
git mergetool
```
Configurar una herramienta mergetool es una muy buena practica para controlar visualmente los cambios, me permito listar algunas que conozco y recomiendo:

- GitLens (VSCode)
- Meld
- GitKraken (Pago)

- Mensajes claros: si se usa la vía A, en el commit de merge deja un mensaje que documente el contexto, recordar que esta rama no sera promovida a ningun entorno mas alla del que causo el conflicto, es un apoyo para validar convergencia, eventualmente el mismo conflicto se resolvera en la preparacion de la rama candidata siempre que aparezca la necesidad.

```
Integrate: Feature AB1234 into develop (resolve conflicts in X,Y,Z)
```
