# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

# HU-03 | Obtener recomendación principal de proveedor de envío

# HU-04 | Obtener opciones alternativas de proveedores

# HU-04 | Consultar opciones alternativas

## Objetivo de la historia
Permitir al usuario visualizar opciones alternativas de proveedores de transporte para compararlas con la recomendación principal y elegir la opción más conveniente.

## Subtareas DEV

### Backend
- Reutilizar `RecomendacionResponse` y `CotizacionResponse` para exponer las opciones alternativas junto con la recomendación principal.

### Frontend

#### Vista / UI
- Mostrar la recomendación principal destacada.
- Mostrar la lista de opciones alternativas de forma separada de la recomendación principal.
- Mostrar en cada alternativa la información relevante para la comparación:
  - proveedor
  - costo
  - tiempo de entrega
- Permitir la selección de un proveedor alternativo desde la interfaz.

#### Navegación
- Agregar acción para seleccionar cualquiera de las opciones alternativas.

#### Pruebas
- Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
- Diseñar casos de prueba para visualización de alternativas y ausencia de alternativas.

### Validación técnica y funcional
- Verificar que las opciones alternativas se muestren separadas de la recomendación principal.
- Validar que cada alternativa muestre proveedor, costo y tiempo de entrega.
- Verificar que la recomendación principal no se repita dentro de la lista de alternativas.
- Validar la selección de una opción alternativa desde la interfaz.
- Ejecutar pruebas funcionales y registrar hallazgos.

# HU-05 | Seleccionar y confirmar proveedor
