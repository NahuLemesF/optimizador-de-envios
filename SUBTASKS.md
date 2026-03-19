# Subtasks

## HU-01 | Registrar pedido de envío

### Objetivo de la historia
Permitirle al usuario agregar pedido para calcular y obtener una recomendación sobre cual proveedor de transporte es más adecuado de acuerdo a sus necesidades

---

### Subtareas DEV

#### Backend

**Modelo o entidad**

Definir modelo Pedido:
- origen (nombre, lat, lon)
- destino (nombre, lat, lon)
- peso
- unidadPeso como enum (GRAMOS, KILOGRAMOS, LIBRAS)
- pesoEnKg
- distancia (km)

## HU-02 | Definir prioridad del envío

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
