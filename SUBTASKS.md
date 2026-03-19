# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

# HU-03 | Obtener recomendación principal de proveedor de envío

## Objetivo de la historia
Permitir al usuario obtener la mejor opción de envío según la prioridad seleccionada (menor costo o menor tiempo de entrega).

## Subtareas DEV

### Backend
- Crear los DTOs necesarios para solicitar y devolver la recomendación.
- Configurar los proveedores mock y sus valores de cotización.
- Implementar la integración simulada con los proveedores mediante adapter.
- Implementar el servicio de cotización para consultar todos los proveedores disponibles.
- Implementar el motor de recomendación según prioridad y reglas de desempate.
- Exponer el endpoint `POST /recomendacion`.
- Realizar pruebas de cobertura e integración.

### Frontend
- Crear la pantalla de resultados con la recomendación principal destacada.
- Consumir el endpoint `POST /recomendacion` utilizando los datos almacenados en el estado global.
- Mostrar la recomendación principal en la interfaz.
- Agregar la navegación para seleccionar el proveedor recomendado.

## Subtareas QA

### Análisis y diseño
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
- Diseñar casos de prueba para recomendación por menor costo, menor tiempo y reglas de desempate.

### Validación técnica y funcional
- Verificar el funcionamiento del endpoint `POST /recomendacion`.
- Validar que la recomendación principal corresponda a la prioridad seleccionada.
- Verificar la correcta aplicación de las reglas de desempate.
- Validar la pantalla de resultados y la visualización de la recomendación principal.
- Ejecutar pruebas funcionales del flujo de recomendación y registrar hallazgos.

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
