# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

# HU-03 | Obtener recomendación principal de proveedor de envío

# HU-04 | Obtener opciones alternativas de proveedores

# HU-05 | Seleccionar y confirmar proveedor

## Objetivo de la historia
Permitir al usuario seleccionar un proveedor de envío y confirmar su selección para.

## Subtareas DEV

### Backend
- Crear el modelo y los DTOs necesarios para la confirmación del pedido.
- Implementar las validaciones de campos obligatorios y proveedor seleccionado.
- Recalcular cotizaciones y construir la entidad final del pedido.
- Implementar la persistencia del pedido mediante repositorio.
- Exponer el endpoint `POST /pedidos/confirmar`.
- Realizar pruebas unitarias y de integración.

### Frontend
- Implementar la opción para confirmar el proveedor seleccionado.
- Consumir el endpoint `POST /pedidos/confirmar` enviando los datos necesarios.
- Redirigir a la pantalla de confirmación cuando la operación sea exitosa.
- Manejar errores enviados por el backend.
- Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
- Diseñar casos de prueba para confirmación exitosa, ausencia de selección, proveedor inválido y persistencia del pedido.

### Validación técnica y funcional
- Verificar el funcionamiento del endpoint `POST /pedidos/confirmar`.
- Validar la persistencia correcta del pedido y la respuesta devuelta por el sistema.
- Verificar la selección y confirmación del proveedor en frontend, incluyendo navegación y manejo de errores.
- Ejecutar pruebas funcionales del flujo completo de confirmación.
- Registrar hallazgos y validar el cumplimiento de los criterios de aceptación.