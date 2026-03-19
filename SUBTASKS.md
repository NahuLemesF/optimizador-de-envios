# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

## Objetivo de la historia
Permitir al usuario seleccionar el criterio de optimización del envío para que el sistema guarde su preferencia y la utilice en el cálculo de la recomendación.

## Subtareas DEV

### Backend
- Extender el modelo Pedido para incluir el atributo prioridad.
- Crear y ajustar los DTOs necesarios para manejar la prioridad.
- Implementar validación de prioridad obligatoria.
- Asociar la prioridad al pedido en memoria.
- Exponer el endpoint POST /pedidos/prioridad.
- Realizar pruebas unitarias y de cobertura.

### Frontend
- Implementar pantalla de selección de prioridad (económico o rápido).
- Validar que el usuario seleccione una opción antes de continuar.
- Guardar la prioridad en el estado global.
- Consumir el endpoint POST /pedidos/prioridad.
- Manejar errores enviados por el backend.
- Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
- Revisar que la HU, reglas de negocio y criterios de aceptación sean claros y testeables.
- Diseñar casos de prueba para selección de prioridad y validación de obligatoriedad.

### Validación técnica y funcional
- Verificar el funcionamiento del endpoint POST /pedidos/prioridad.
- Validar que la prioridad se guarde correctamente en memoria.
- Verificar la selección de prioridad en frontend y su almacenamiento en el estado global.
- Validar el flujo completo de selección de prioridad y manejo de errores.
- Ejecutar pruebas funcionales y registrar hallazgos.

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
