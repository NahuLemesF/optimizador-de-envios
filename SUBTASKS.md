# Subtasks - Optimizador de Envíos

---

# HU-01 | Registrar pedido de envío

## Objetivo de la historia
Permitirle al usuario agregar pedido para calcular y obtener una recomendación sobre cual proveedor de transporte es más adecuado de acuerdo a sus necesidades

## Subtareas DEV

### Backend
- Definir el modelo Pedido y los DTOs necesarios para el registro del envío.
- Implementar validaciones de campos obligatorios, rango de peso y cobertura en Colombia.
- Implementar conversión de unidades de peso y normalización a kilogramos.
- Integrar el servicio externo para autocompletado de ubicaciones y cálculo de distancia.
- Implementar endpoints GET /locations/autocomplete y POST /pedido.
- Realizar pruebas unitarias y de cobertura para las capas del backend.

### Frontend
- Implementar formulario de registro con origen, destino, peso y unidad.
- Implementar autocompletado para origen y destino consumiendo el endpoint correspondiente.
- Validar campos obligatorios y formato del peso.
- Consumir endpoint POST /pedido y almacenar la información en el estado global.
- Permitir la navegación al siguiente paso del flujo.
- Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
- Revisar que la HU, reglas de negocio y criterios de aceptación sean claros y testeables.
- Diseñar casos de prueba para registro exitoso, validación de campos, peso fuera de rango y cobertura geográfica.

### Validación técnica y funcional
- Verificar el funcionamiento de los endpoints GET /locations/autocomplete y POST /pedido.
- Validar el autocompletado y la restricción de ubicaciones dentro de Colombia.
- Verificar la conversión de unidades y cálculo de distancia.
- Validar el flujo completo desde frontend, incluyendo almacenamiento en estado global.
- Ejecutar pruebas funcionales y registrar hallazgos.

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
