# Subtasks

# HU-01 | Registrar pedido de envío

# HU-02 | Definir prioridad del envío

# HU-03 | Obtener recomendación principal de proveedor de envío

## Objetivo de la historia
Permitir al usuario obtener la mejor opción de envío según la prioridad seleccionada (menor costo o menor tiempo de entrega).

## Subtareas DEV

### Backend

#### DTOs
- Crear `RecomendacionRequest`:
  - Contiene toda la información guardada en el estado global
  - origen (lat, lon)
  - destino (lat, lon)
  - pesoKg
  - distancia
  - prioridad

- Crear `CotizacionResponse` (sirve para representar la cotización de un solo proveedor):
  - proveedor
  - costo
  - tiempoEntrega

- Crear `RecomendacionResponse`:
  - recomendacionPrincipal
  - opcionesAlternativas

#### Configuración de mocks con `.yml`
- Dado que el sistema se crea para ser utilizado con proveedores como FedEx, DHL, etc., se mockearán valores en un `application.yml`.
- Valores a guardar por proveedor:
  - costoBase
  - precioPorKg
  - precioPorKm
  - kmPorDia

- Crear clase `ProveedorConfig` y `ProveedorProperties`.

#### Integración externa simulada mediante Adapter
- Crear interfaz `ProveedorClient` con el método `cotizar` para cotizar un pedido.

- Implementar:
  - `FedexAPIMock`
  - `DHLAPIMock`
  - `LocalAPIMock`

- A estas implementaciones se les inyectará la configuración desde el `.yml`.

#### Servicio de cotización
- Crear `CotizacionService`.
- Inyectar la lista de `ProveedorClient`.
- Ejecutar la cotización en todos los proveedores.
- Retornar la lista de resultados.

#### Motor de recomendación
- Crear interfaz `EstrategiaRecomendacion`.
- Implementar:
  - `EstrategiaCosto`
  - `EstrategiaTiempo`

- Crear `EstrategiaFactory`.

- Crear `MotorRecomendacionService`:
  - selecciona la estrategia
  - obtiene la mejor opción
  - maneja empates

#### Endpoint
- Crear `POST /recomendacion`:
  - recibe `RecomendacionRequest`
  - llama a `CotizacionService`
  - llama a `MotorRecomendacionService`
  - retorna `RecomendacionResponse`

#### Pruebas
- Realizar pruebas de cobertura.
- Realizar pruebas de integración para verificar el correcto funcionamiento entre capas.

### Frontend

#### Vista / UI
- Crear pantalla de resultados con la recomendación principal destacada.

#### Lógica del cliente
- Consumir `POST /recomendacion`.
- Enviar los datos del pedido almacenados en el estado global.

#### Navegación
- Agregar botón para seleccionar el proveedor de la opción recomendada.

### Subtareas QA

#### Análisis funcional
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros, consistentes y testeables.
- Validar que la lógica de recomendación esté alineada con el PRD, el alcance del MVP y la prioridad seleccionada por el usuario.
- Verificar la coherencia entre pedido, cotización, recomendación principal y opciones alternativas.

#### Diseño de casos de prueba
- Diseñar casos de prueba para recomendación principal por menor costo.
- Diseñar casos de prueba para recomendación principal por menor tiempo de entrega.
- Diseñar casos de prueba para empate en menor costo.
- Diseñar casos de prueba para empate en menor tiempo de entrega.
- Diseñar casos de prueba para escenarios con múltiples proveedores disponibles.
- Diseñar casos de prueba para escenarios donde solo exista una opción válida.

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
