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

## HU-02 | Definir prioridad del envío

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
