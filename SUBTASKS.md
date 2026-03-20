# Subtasks - Optimizador de Envíos

---

# HU-01 | Registrar pedido de envío

## Objetivo de la historia
Permitirle al usuario agregar pedido para calcular y obtener una recomendación sobre cual proveedor de transporte es más adecuado de acuerdo a sus necesidades

## Subtareas DEV

### Backend
T-01 | Definir el modelo Pedido y los DTOs necesarios para el registro del envío.
T-02 | Implementar validaciones de campos obligatorios, rango de peso y cobertura en Colombia.
T-03 | Implementar conversión de unidades de peso y normalización a kilogramos.
T-04 | Integrar un servicio externo de geolocalización para autocompletado de ubicaciones y cálculo de distancia (*openRouteService*).
T-05 | Implementar endpoints `GET /locations/autocomplete` y `POST /pedido`.
T-06 | Realizar pruebas unitarias y de cobertura para las capas del backend.

### Frontend
T-07 | Implementar formulario de registro con origen, destino, peso y unidad.
T-08 | Implementar autocompletado para origen y destino consumiendo el endpoint correspondiente.
T-09 | Validar campos obligatorios y formato del peso.
T-10 | Consumir endpoint `POST /pedido` y almacenar la información en el estado global.
T-11 | Permitir la navegación al siguiente paso del flujo.
T-12 | Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
T-13 (QA) | Revisar que la HU, reglas de negocio y criterios de aceptación sean claros y testeables.
T-14 (QA) | Diseñar casos de prueba para registro exitoso, validación de campos, peso fuera de rango y cobertura geográfica.

### Validación técnica y funcional
T-15 (QA) | Verificar el funcionamiento de los endpoints `GET /locations/autocomplete` y `POST /pedido`.
T-16 (QA) | Validar el autocompletado y la restricción de ubicaciones dentro de Colombia.
T-17 (QA) | Verificar la conversión de unidades y cálculo de distancia.
T-18 (QA) | Validar el flujo completo desde frontend, incluyendo almacenamiento en estado global.
T-19 (QA) | Ejecutar pruebas funcionales y registrar hallazgos.

## Estimación: 5 puntos

### Justificación:
- **DEV:** Esfuerzo medio. Se implementa el registro del pedido con validaciones de datos (origen, destino y peso), construcción de DTOs y endpoint. La complejidad radica en asegurar la consistencia de los datos y su correcto guardado en el estado global. En el frontend, se desarrolla el formulario con sus correspondientes validaciones.
- **QA**: Esfuerzo medio. Se deben cubrir casos funcionales del registro del pedido, validar campos obligatorios y verificar la correcta respuesta del backend. Los escenarios son bastante simples, por lo que no requiere pruebas complejas.

---

# HU-02 | Definir prioridad del envío

## Objetivo de la historia
Permitir al usuario seleccionar el criterio de optimización del envío para que el sistema guarde su preferencia y la utilice en el cálculo de la recomendación.

## Subtareas DEV

### Backend
T-01 | Extender el modelo Pedido para incluir el atributo prioridad.
T-02 | Crear y ajustar los DTOs necesarios para manejar la prioridad.
T-03 | Implementar validación de prioridad obligatoria.
T-04 | Asociar la prioridad al pedido en memoria.
T-05 | Exponer el endpoint POST /pedidos/prioridad.
T-06 | Realizar pruebas unitarias y de cobertura.

### Frontend
T-07 | Implementar pantalla de selección de prioridad (económico o rápido).
T-08 | Validar que el usuario seleccione una opción antes de continuar.
T-09 | Guardar la prioridad en el estado global.
T-10 | Consumir el endpoint POST /pedidos/prioridad.
T-11 | Manejar errores enviados por el backend.
T-12 | Realizar pruebas unitarias y de cobertura.


## Subtareas QA

### Análisis y diseño
T-13 (QA) | Revisar que la HU, reglas de negocio y criterios de aceptación sean claros y testeables.
T-14 (QA) | Diseñar casos de prueba para selección de prioridad y validación de obligatoriedad.

### Validación técnica y funcional
T-15 (QA) | Verificar el funcionamiento del endpoint POST /pedidos/prioridad.
T-16 (QA) | Validar que la prioridad se guarde correctamente en memoria.
T-17 (QA) | Verificar la selección de prioridad en frontend y su almacenamiento en el estado global.
T-18 (QA) | Validar el flujo completo de selección de prioridad y manejo de errores.
T-19 (QA) | Ejecutar pruebas funcionales y registrar hallazgos.

## Estimación: 3 puntos

### Justificación:
- **DEV:** Esfuerzo bajo. Se actualiza el modelo del pedido para incluir la prioridad y se implementa un endpoint para actualizar esta información. En el frontend, se desarrolla una pantalla sencilla para seleccionar la prioridad, con validación de selección y almacenamiento en el estado global.
- **QA**: Esfuerzo bajo. Se deben validar casos funcionales de selección de prioridad y obligatoriedad. El proceso es bastante directo, por lo que no requiere pruebas complejas.

---

# HU-03 | Obtener recomendación principal de proveedor de envío

## Objetivo de la historia
Permitir al usuario obtener la mejor opción de envío según la prioridad seleccionada (menor costo o menor tiempo de entrega).

## Subtareas DEV

### Backend
T-01 | Crear los DTOs necesarios para solicitar y devolver la recomendación.
T-02 | Configurar los proveedores mock y sus valores de cotización.
T-03 | Implementar la integración simulada con los proveedores mediante el patrón adapter.
T-04 | Implementar el servicio de cotización para consultar todos los proveedores disponibles.
T-05 | Implementar el motor de recomendación según prioridad y reglas de desempate utilizando los patrones strategy y factory.
T-06 | Exponer el endpoint `POST /recomendacion`.
T-07 | Realizar pruebas de cobertura e integración.

### Frontend
T-08 | Crear la pantalla de resultados con la recomendación principal destacada.
T-09 | Consumir el endpoint `POST /recomendacion` utilizando los datos almacenados en el estado global.
T-10 | Mostrar la recomendación principal en la interfaz.
T-11 | Agregar la navegación para seleccionar el proveedor recomendado.

## Subtareas QA

### Análisis y diseño
T-12 (QA) | Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
T-13 (QA) | Diseñar casos de prueba para recomendación por menor costo, menor tiempo y reglas de desempate.

### Validación técnica y funcional
T-14 (QA) | Verificar el funcionamiento del endpoint `POST /recomendacion`.
T-15 (QA) | Validar que la recomendación principal corresponda a la prioridad seleccionada.
T-16 (QA) | Verificar la correcta aplicación de las reglas de desempate.
T-17 (QA) | Validar la pantalla de resultados y la visualización de la recomendación principal.
T-18 (QA) | Ejecutar pruebas funcionales del flujo de recomendación y registrar hallazgos.

## Estimación: 8 puntos

### Justificación:
- **DEV:** Esfuerzo alto. Se implementa la lógica de integración con proveedores de envío, el motor de recomendación y el endpoint para obtener la recomendación principal, utilizando los patrones strategy y factory. En el frontend, se desarrolla la pantalla de resultados y se consume el endpoint para mostrar la recomendación al usuario.
- **QA**: Esfuerzo medio-alto. Se deben validar casos funcionales de recomendación según prioridad y reglas de desempate. El proceso es más complejo debido a la lógica de recomendación, por lo que requiere pruebas detalladas para asegurar la correcta aplicación de las reglas.

---

# HU-04 | Consultar opciones alternativas

## Objetivo de la historia
Permitir al usuario visualizar opciones alternativas de proveedores de transporte para compararlas con la recomendación principal y elegir la opción más conveniente.

## Subtareas DEV

### Backend
T-01 | Reutilizar `RecomendacionResponse` y `CotizacionResponse` para exponer las opciones alternativas junto con la recomendación principal.

### Frontend

#### Vista / UI
T-02 | Mostrar la recomendación principal destacada.
T-03 | Mostrar la lista de opciones alternativas de forma separada de la recomendación principal.
T-04 | Mostrar en cada alternativa la información relevante para la comparación:
  - proveedor
  - costo
  - tiempo de entrega
T-05 | Permitir la selección de un proveedor alternativo desde la interfaz.
T-06 | Agregar acción para seleccionar cualquiera de las opciones alternativas.
T-07 | Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
T-08 (QA) | Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
T-09 (QA) | Diseñar casos de prueba para visualización de alternativas y ausencia de alternativas.

### Validación técnica y funcional
T-10 (QA) | Verificar que las opciones alternativas se muestren separadas de la recomendación principal.
T-11 (QA) | Validar que cada alternativa muestre proveedor, costo y tiempo de entrega.
T-12 (QA) | Verificar que la recomendación principal no se repita dentro de la lista de alternativas.
T-13 (QA) | Validar la selección de una opción alternativa desde la interfaz.
T-14 (QA) | Ejecutar pruebas funcionales y registrar hallazgos.

## Estimación: 3 puntos

### Justificación:
- **DEV:** Esfuerzo medio-bajo. Se reutilizan los DTOs existentes para mostrar las opciones alternativas en el frontend, con una separación clara de la recomendación principal. Se implementa la lógica para mostrar la información relevante de cada alternativa y permitir su selección.
- **QA**: Esfuerzo bajo. Se deben validar casos funcionales de visualización de alternativas y selección de una opción alternativa. El proceso es bastante directo, por lo que no requiere pruebas complejas.

---

# HU-05 | Seleccionar y confirmar proveedor

## Objetivo de la historia
Permitir al usuario seleccionar un proveedor de envío y confirmar su selección para completar el proceso de pedido.

## Subtareas DEV

### Backend
T-01 | Crear el modelo y los DTOs necesarios para la confirmación del pedido.
T-02 | Implementar las validaciones de campos obligatorios y proveedor seleccionado.
T-03 | Recalcular cotizaciones y construir la entidad final del pedido.
T-04 | Implementar la persistencia del pedido mediante repositorio.
T-05 | Exponer el endpoint `POST /pedidos/confirmar`.
T-06 | Realizar pruebas unitarias y de integración.

### Frontend
T-07 | Implementar la opción para confirmar el proveedor seleccionado.
T-08 | Consumir el endpoint `POST /pedidos/confirmar` enviando los datos necesarios.
T-09 | Redirigir a la pantalla de confirmación cuando la operación sea exitosa.
T-10 | Manejar errores enviados por el backend.
T-11 | Realizar pruebas unitarias y de cobertura.

## Subtareas QA

### Análisis y diseño
T-12 (QA) | Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros y testeables.
T-13 (QA) | Diseñar casos de prueba para confirmación exitosa, ausencia de selección, proveedor inválido y persistencia del pedido.

### Validación técnica y funcional
T-14 (QA) | Verificar el funcionamiento del endpoint `POST /pedidos/confirmar`.
T-15 (QA) | Validar la persistencia correcta del pedido y la respuesta devuelta por el sistema.
T-16 (QA) | Verificar la selección y confirmación del proveedor en frontend, incluyendo navegación y manejo de errores.
T-17 (QA) | Ejecutar pruebas funcionales del flujo completo de confirmación.
T-18 (QA) | Registrar hallazgos y validar el cumplimiento de los criterios de aceptación.

## Estimación: 5 puntos
### Justificación:
- **DEV:** Esfuerzo medio. Se implementa la lógica para confirmar el pedido, incluyendo validaciones, recalculo de cotizaciones y persistencia. En el frontend, se desarrolla la funcionalidad para confirmar la selección del proveedor y manejar la navegación y errores.
- **QA**: Esfuerzo medio. Se deben validar casos funcionales de confirmación del pedido, incluyendo validación de selección, manejo de errores y persistencia. El proceso es más complejo debido a la confirmación del pedido, por lo que requiere pruebas detalladas para asegurar la correcta aplicación de las reglas y la persistencia de los datos.

---
    