# Subtasks

## HU-01 | Registrar pedido de envío

## HU-02 | Definir prioridad del envío

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor

### Objetivo de la historia
Permitir al usuario seleccionar un proveedor de envío y confirmar su selección para persistir el pedido con la información final validada

---

### Subtareas DEV

#### Backend

**Modelo**
- Crear la entidad PedidoEntity con:
  - origen (nombre, lat, lon)
  - destino (nombre, lat, lon)
  - pesoKg
  - distancia
  - prioridad
  - proveedorSeleccionado
  - costoFinal
  - tiempoEntrega
  - fechaCreacion

---

**DTO’s**
- Crear ConfirmacionPedidoRequest con:
  - origen
  - destino
  - pesoKg
  - distancia
  - prioridad
  - proveedorSeleccionado

- Crear ConfirmacionPedidoResponse:
  - idPedido
  - proveedorSeleccionado
  - costoFinal
  - tiempoEntrega
  - mensajeConfirmacion

---

**Servicio**
- Validar campos obligatorios
- Validar proveedor seleccionado
- Recalcular cotizaciones utilizando CotizacionService y MotorRecomendacionService
- Construir la entidad PedidoEntity

---

**Persistencia**
- Crear PedidoRepository con JPA
- Guardar el pedido

---

**Endpoint**
- Crear endpoint POST /pedidos/confirmar

---

**Pruebas**
- Pruebas unitarias
- Pruebas de integración

---

#### Frontend

**Vista / UI**
- En la pantalla de selección de la opción debe haber un botón para seleccionarlo

---

**Lógica**
- Consumir endpoint POST /pedidos/confirmar enviando:
  - proveedor seleccionado
  - origen
  - destino
  - peso
  - distancia
  - prioridad

---

**Navegación**
- Si la operación es exitosa, redirigir a pantalla de confirmación con el responseDTO

---

**Pruebas y manejo de errores**
- Manejar errores enviados por el backend
- Pruebas unitarias
- Pruebas de cobertura
