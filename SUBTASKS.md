# Subtasks - Optimizador de Envíos

---

# HU-01 | Registrar pedido de envío

## Objetivo de la historia
Permitirle al usuario agregar pedido para calcular y obtener una recomendación sobre cual proveedor de transporte es más adecuado de acuerdo a sus necesidades

## Subtareas DEV

### Backend

**Modelo o entidad**

Definir modelo **Pedido**:
- origen (nombre, lat, lon)
- destino (nombre, lat, lon)
- peso
- unidadPeso como enum (GRAMOS, KILOGRAMOS, LIBRAS)
- pesoEnKg
- distancia (km)

**DTO’s**
- PedidoRequest con origen, destino, peso y unidadPeso
- PedidoResponse con los mismos datos 
- LocationResponse con nombre para tener en lista el origen y el destino con su lat y lon

**Regla o servicio de dominio**
- Validar campos obligatorios (usando DTO o dominio)
- Mapear PedidoRequest → Pedido
- Implementar conversión de unidades a Kg
- Normalizar peso a pesoEnKg
- Validar rango permitido (0.001 - 70 Kg)
- Validar que la API unicamente traiga lugares de Colombia
- Orquestar cálculo de distancia usando servicio externo
- Mapear Pedido → PedidoResponse

**Integracion Externa (OpenRouteService)**
- Crear metodo de autocomplete que retorne los diferentes lugares de acuerdo al texto puesto por el cliente para tener nombre, lat y lon
- Crear metodo getDistance para determinar la distancia que existe entre origen y destino

**Persistencia**
- Manejo en memoria

**Endpoint o caso de uso**
- Crear endpoint GET /locations/autocomplete para retornar la lista de las locaciones encontradas por la API
- Crear endpoint POST /pedido donde se recibe el requestDTO y retorna el responseDTO

**Pruebas unitarias técnicas**
- Crear pruebas unitarias para validaciones de datos (campos obligatorios, peso)
- Crear pruebas unitarias de cobertura para las diferentes capas

### Frontend

**Vista**
- Crear formulario de registro:
  - Input origen
  - Input destino
  - Input peso
  - Selector de unidad (g, kg, lb)

**Logica de cliente**
- Implementar autocompletado:
  - Llamar al endpoint de autocomplete (usando debounce)
  - Mostrar sugerencias
  - Guardar selección
  - Debe funcionar para origen y destino

- Validar campos obligatorios y el formato del peso (numérico)

- Consumir endpoint POST para guardar el pedido en estado Global

- El estado global debe guardar:
  - origen
  - destino
  - pesoKg
  - distancia

**Pruebas Unitarias**
- Validación de inputs
- Persistencia del estado del pedido en el estado global

## Subtareas QA

### Análisis funcional
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros, consistentes y testeables.
- Validar que el flujo de registro del pedido esté alineado con el PRD y el alcance del MVP.

### Diseño de casos de prueba
- Diseñar casos de prueba para registro exitoso, campos obligatorios vacíos, peso fuera de rango y ubicaciones fuera de Colombia.
- Diseñar casos de prueba para conversión de unidades de peso a kilogramos.
- Diseñar casos de prueba para cálculo de distancia entre origen y destino.

### Validación backend
- Verificar el funcionamiento del endpoint `GET /locations/autocomplete` y del endpoint `POST /pedido`.
- Validar que el autocomplete retorne únicamente lugares de Colombia.
- Validar que el sistema normalice correctamente el peso y rechace valores fuera del rango permitido.

### Validación frontend
- Verificar el formulario de registro con origen, destino, peso y unidad.
- Validar el funcionamiento del autocompletado y las validaciones de campos obligatorios.
- Verificar que el estado global almacene correctamente los datos del pedido.

### Pruebas y evidencia
- Preparar datos de prueba para escenarios válidos, inválidos y de borde.
- Ejecutar pruebas funcionales del flujo de registro del pedido.
- Registrar hallazgos y validar el cumplimiento de los criterios de aceptación.

---

## HU-02 | Definir prioridad del envío

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
