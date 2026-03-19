# Subtasks

## HU-01 | Registrar pedido de envío

## HU-02 | Definir prioridad del envío

## HU-03 | Obtener recomendación principal de proveedor de envío

### Objetivo de la historia
Permitir al usuario obtener la mejor opcion de envio segun la prioridad seleccionada (menor costo o menor tiempo)

---

### Subtareas DEV

#### Backend

**DTO’s**
- Crear RecomendacionRequest:
  - Contiene todo lo guardado del estado global
  - Origen (lat, lon)
  - Destino (lat, lon)
  - pesoKg
  - distancia
  - prioridad

- Crear CotizacionResponse (sirve para tener lo de un solo proveedor):
  - proveedor
  - costo
  - tiempoEntrega

- Crear RecomendacionResponse:
  - recomendacionPrincipal
  - opcionesAlternativas

---

**Configuracion de Mock con .yml**
- Dado que el sistema se crea para ser utilizado con Fedex, DHL, etc, se mockean valores en un application.yml
- Valores a guardar por proveedor:
  - costoBase
  - precioPorKg
  - precioPorKm
  - kmPorDia

- Crear clase ProveedorConfig y ProveedorProperties

---

**Integracion Externa (Simulada) haciendo uso de Adapter**
- Crear interfaz ProveedorClient con metodo cotizar para cotizar pedido

- Implementar:
  - FedexAPIMock
  - DHLAPIMock
  - LocalAPIMock

- A los cuales se les inyectara el .yml

---

**Servicio de cotizacion**
- Crear CotizacionService
- Inyectar la lista de ProveedorClient
- Ejecutar cotizacion en todos los proveedores
- Retornar lista de resultados

---

**Motor de Recomendacion**
- Crear interfaz EstrategiaRecomendacion
- Implementar:
  - EstrategiaCosto
  - EstrategiaTiempo

- Crear EstrategiaFactory

- Crear MotorRecomendacionService:
  - Selecciona la estrategia
  - Obtiene la mejor opcion
  - Maneja empates

---

**Endpoint**
- Crear POST /recomendacion:
  - Recibe RecomendacionRequest
  - Llama a CotizacionService
  - Llama a MotorRecomendacionService
  - Retorna RecomendacionResponse

---

**Pruebas**
- Realizar pruebas de cobertura
- Realizar pruebas de integracion para verificar el correcto funcionamiento entre capas

---

#### Frontend

**Vista / UI**
- Pantalla de resultados con la recomendacion principal destacada

---

**Logica del cliente**
- Consumir POST /recomendacion
- Enviar datos del pedido que estan en el estado global

---

**Navegación**
- Boton para seleccionar proveedor de la opcion recomendada

---

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
