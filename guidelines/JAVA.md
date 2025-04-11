[ **[Volver al Menú Principal](../README.md)** ]

# Lineamientos para el Desarrollo Java

Este documento define los lineamientos técnicos para el desarrollo de aplicaciones Java. Se orienta a proyectos con una arquitectura modular, en la cual la lógica reside en módulos, y se comunica a través de flujos estructurados de datos usando objetos de transporte bien definidos.

## Buenas Prácticas Generales

### Estructura del Código y Separación de Responsabilidades

- Mantener una clara separación entre WebVO, DTO y Entity.
- No implementar lógica de negocio en WebVO ni en entidades persistentes (Entity).
- Toda la lógica de negocio debe residir exclusivamente en los módulos.
- El endpoint actúa como un punto de entrada delgado que transfiere datos, no procesa lógica.

### Documentación JavaDoc

#### Clases

- Cada clase pública debe estar documentada con un bloque JavaDoc que incluya:
  - Propósito general de la clase.
  - Comportamiento esperado.
  - Componentes importantes usados internamente (por ejemplo: `EntityManager`, `SessionContext`, etc.).

```java
/**
 * Clase responsable de gestionar la lógica de negocio relacionada con convenios.
 * Usa transformadores para convertir datos entre WebVO, DTO y Entity.
 * Interactúa con la base de datos usando EntityManager.
 *
 * @author Equipo de Desarrollo
 * @version 1.0
 */
```

#### Métodos

- Todo método público debe tener JavaDoc detallado con:
  - `@param`: Descripción de cada parámetro.
  - `@return`: Qué devuelve y bajo qué condiciones.
  - `@throws`: Excepciones relevantes que puede lanzar.
  - `@RolesAllowed`: Si aplica, indicar roles requeridos para invocar el método.

Ejemplo:

```java
/**
 * Obtiene un convenio por ID desde el módulo de convenios.
 * Este método consulta la base de datos usando el módulo de negocio.
 *
 * @param convenioId Identificador único del convenio a recuperar.
 * @return ConvenioWebVO con la información del convenio encontrado.
 * @throws MonitoriasException si ocurre un error durante la consulta o el convenio no existe.
 */
```

### Control de Errores

- Capturar excepciones específicas si es posible.
- Lanzar excepciones de negocio customizadas.
- Nunca exponer trazas internas al cliente.

### Seguridad

- Usar `@RolesAllowed` para proteger métodos según perfiles específicos.
- Evitar el uso de `@PermitAll` salvo que sea estrictamente necesario.

---

## Principios de Arquitectura

- No se emplean capas de servicio ni controladores (`controller`).
- Toda la lógica se organiza en módulos que interactúan con datos a través de transformaciones.

---

## Flujo de Datos y Transformación

### Objetos Involucrados

1. **WebVO**: Estructura usada en endpoints para enviar y recibir datos del cliente.
2. **DTO**: Objeto intermedio donde se aplica la lógica de negocio.
3. **Entity**: Representación persistente usada por JPA para interactuar con la base de datos.

### Transformadores

Se deben usar clases específicas para transformar datos:

- `AgreementTransformationServices`: Transforma entre WebVO y DTO, y viceversa.
- `AgreementTransformationLogic`: Transforma entre DTO y Entity, y viceversa.

Esta separación facilita mantenimiento, validaciones y reutilización.

---

## Persistencia y Contextos

Cada módulo debe incluir las siguientes inyecciones:

```java
@PersistenceContext(unitName = "Monitorias-persistance")
protected EntityManager entityManager;

@Resource
private SessionContext sctx;

@Context
private SecurityContext ctx;
```

### Persistencia de Datos

Para crear un nuevo convenio:

```java
entityManager.persist(newAgreement);
entityManager.flush();
```

- `flush()` asegura que los cambios se sincronicen de inmediato con la base de datos.
- Útil cuando se requiere conocer el ID generado o ejecutar lógica post-persistencia.

---

## Interceptores y Auditoría

Se recomienda el uso de interceptores para auditoría y trazabilidad:

```java
@Interceptors(AgreementInterceptor.class)
@IAgreementEventsLog(Monitorias_Engagement_Events.CREATE_AGREEMENT)
```

- Permite registrar eventos automáticamente (crear, modificar, eliminar).
- Útil para trazabilidad y validación de operaciones sensibles.

---

## Seguridad en Endpoints

Uso recomendado de anotaciones de acceso:

```java
@GET
@Produces(MediaType.APPLICATION_JSON)
@Consumes(MediaType.APPLICATION_JSON)
@RolesAllowed({"Administrador", "AdministradorConvenios", "GestorFinanciero"})
@Path("/getConvenioById/{convenioId}")
public ConvenioWebVO getConvenioById(@PathParam("convenioId") Integer convenioId) throws MonitoriasException {
    try {
        return MonitoriasEngagementFactory.getInstance().getAgreementBusinessService()
                .getAgreementById(convenioId);
    } catch (Exception e) {
        throw new MonitoriasEngagementWebServiceException(Monitorias_Modules.ENGAGEMENT,
                Monitorias_Engagement_Entities.ENGAGEMENT, MonitoriasOperationType.READ,
                Thread.currentThread().getStackTrace()[1], e, Status.INTERNAL_SERVER_ERROR);
    }
}
```

---

[ **[Volver al Menú Principal](../README.md)** ]