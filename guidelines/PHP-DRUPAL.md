[ **[Volver al Menú Principal](MAIN.md)** ]

# ✅ Lineamientos de desarrollo para proyectos Drupal 11 (Estrategia Web)

---

## 🔸 1. Estándares Generales de PHP

- Usar **PHP 8.3 o superior**.
- Seguir la especificación [**PSR-12**](https://www.php-fig.org/psr/psr-12/).
- Declarar siempre los **tipos de retorno** en funciones y métodos.

```php
public function getTitle(): string {
    return 'Página principal';
}
```

- Aplicar el **principio de responsabilidad única (SRP)** para funciones y métodos.
- Escribir nombres **descriptivos y en inglés** para funciones, clases, variables y constantes.
- Separar responsabilidades entre `Services`, `Controllers`, `Forms`, `Plugins`, etc.
- Documentar clases y métodos usando **PHPDoc**:

```php
/**
 * Get user roles.
 *
 * @param \Drupal\user\Entity\User $user
 *   The user object.
 *
 * @return string[]
 *   An array of role IDs.
 */
public function getUserRoles(User $user): array {
    return $user->getRoles();
}
```

- Usar **autocarga PSR-4** correctamente.

---

## 🔸 2. Buenas Prácticas en Drupal

- Seguir los [**Drupal Coding Standards**](https://www.drupal.org/docs/develop/standards) usando:
  - Extensión de **VSCode**.
  - Librería `drupal/coder`.

- Mantener código **orientado a objetos (OOP)**.
- Evitar uso directo de `\Drupal::`, preferir **inyección de dependencias**.
- Documentar siempre los **hooks personalizados**.
- Colocar configuraciones en `/config/install` o `/config/optional`, según corresponda.
- Evitar modificar configuraciones en producción; siempre usar:

```bash
drush cim
```

- Validar entidades antes de guardar:

```php
$violations = $entity->validate();
```

- Mantener los módulos personalizados **separados y versionados**.
- Escribir **tests funcionales o unitarios** para nuevos módulos o integraciones.

---

## 🔸 3. Uso Obligatorio de Herramientas de Calidad

- Usar **PHPStan** con nivel mínimo `5` (idealmente `7` u `8`).
- Usar **PHPCS** con los estándares `Drupal` y `DrupalPractice`:

```bash
phpcs --standard=Drupal web/modules/custom
```

- Validar el código antes de hacer merge:
  - `phpcs`
  - `phpstan`
  - `phpunit`
  - `lint`

- Configurar **pipelines CI/CD** que incluyan estos pasos.
- Mantener una **cobertura de pruebas mínima del 80%** cuando aplique.
- Integrar métricas con **SonarQube o SonarCloud** si es posible.

---

## 🔸 4. SonarLint Obligatorio en VS Code

- Instalar la extensión **SonarLint** en VS Code.
- Asociar el workspace al proyecto de **SonarQube/SonarCloud** si está disponible.
- Configurar análisis en tiempo real para:
  - PHP
  - Twig
  - YAML

- Corregir advertencias antes de subir el código.
- Usar SonarLint como **primera línea de defensa** para detectar:
  - Code smells
  - Duplicidad
  - Vulnerabilidades

---

## 🔸 5. Otros Lineamientos Complementarios

- Evitar lógica compleja en archivos `.html.twig`.
- Separar lógica de **backend del renderizado**.
- Mantener estructuras claras:

```
/src/Service
/src/Form
/src/Controller
/src/Plugin
```

- No mezclar lógica de negocio con lógica de presentación.
- Documentar cada módulo personalizado:
  - `README.md` básico
  - Dependencias
  - Objetivo

- Versionar correctamente los módulos:

```yaml
name: 'Mi Módulo Personalizado'
type: module
core_version_requirement: ^11
package: Custom
version: 1.0.0
```

---

_Para más detalles: [Drupal Coding Standards](https://www.drupal.org/docs/develop/standards)_

---

[ **[Volver al Menú Principal](MAIN.md)** ]