# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

## Objetivo de la historia:
Permitir al usuario seleccionar el criterio de optimización del envío para el sistema guarde su preferencia y usarla en el cálculo de la recomendación

## Subtareas DEV

### Backend

#### Modelo:
- Extender en el modelo Pedido para ahora tener el atributo prioridad, que puede ser (`ECONOMICO`, `RAPIDO`).

#### DTO’s:
- **Crear `PrioridadRequest`.** Este DTO recibirá la prioridad seleccionada por el usuario.

- **Actualizar `PedidoResponse` para incluir la prioridad**. Esto permitirá que el frontend tenga acceso a la prioridad seleccionada y pueda mostrarla o usarla según sea necesario.

#### Regla o Servicio:
- Validar que la prioridad sea obligatoria.
- Asociar la prioridad al pedido en memoria.

#### Persistencia o Repositorio:
- Se maneja en memoria.

#### Endpoint o Caso de Uso:
- Crear endpoint `POST /pedidos/prioridad` donde recibe el `PrioridadRequest` y retorna `PedidoResponse` actualizado para guardarlo en el estado global.

#### Pruebas Unitarias:
- Validación de que se tenga que elegir obligatoriamente una de las prioridades.
- Crear pruebas unitarias para alcanzar cobertura.

### Frontend

#### Vista/UI:
- Crear pantalla de selección de prioridad con las opciones de `ECONOMICO`, `RAPIDO`.

#### Lógica del cliente:
- Validar que el usuario tenga que seleccionar una opción.
- Guardar la prioridad en el estado global.
- Manejar errores que envíe el backend.

#### Pruebas Unitarias:
- Selección de prioridad y validar que sea obligatoria.
- Pruebas de cobertura.

## Subtareas QA

### Análisis funcional
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros, consistentes y testeables.
- Validar que la selección de prioridad esté alineada con el PRD y el flujo del MVP.

### Diseño de casos de prueba
- Diseñar casos de prueba para selección válida de prioridad económica.
- Diseñar casos de prueba para selección válida de prioridad rápida.
- Diseñar casos de prueba para intento de continuar sin prioridad seleccionada.
- Diseñar casos de prueba para persistencia de la prioridad en memoria y en el estado global.

### Validación backend
- Verificar el funcionamiento del endpoint `POST /pedidos/prioridad`.
- Validar que la prioridad sea obligatoria.
- Verificar que el pedido en memoria se actualice correctamente con la prioridad seleccionada.
- Validar que la respuesta incluya la prioridad actualizada.
- Verificar el manejo esperado ante errores o datos inválidos.

### Validación frontend
- Verificar la pantalla de selección de prioridad con las opciones `ECONOMICO` y `RAPIDO`.
- Validar que el usuario deba seleccionar una opción para continuar.
- Verificar que la prioridad seleccionada se almacene correctamente en el estado global.
- Validar el manejo de errores enviados por el backend.

### Pruebas y evidencia
- Preparar datos de prueba para escenarios válidos, inválidos y de borde.
- Ejecutar pruebas funcionales del flujo de selección de prioridad.
- Registrar hallazgos y validar el cumplimiento de los criterios de aceptación.

---

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
