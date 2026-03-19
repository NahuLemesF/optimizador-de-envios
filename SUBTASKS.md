# Subtasks

## HU-01 | Registrar pedido de envío

## HU-02 | Definir prioridad del envío

### Objetivo de la historia:
Permitir al usuario seleccionar el criterio de optimización del envío para el sistema guarde su preferencia y usarla en el cálculo de la recomendación

### Subtareas DEV

**Backend**
- **Modelo:**
    - Extender en el modelo Pedido para ahora tener el atributo prioridad, que puede ser (ECONOMICO, RAPIDO)
- **DTO’s:**
    - Crear PrioridadRequest 
    - Actualizar PedidoResponse para incluir la prioridad
- **Regla o Servicio:**
    - Validar que la prioridad sea obligatoria
    - Asociar la prioridad al pedido en memoria
- **Persistencia o Repositorio:**
    - Se maneja en memoria
- **Endpoint o Caso de Uso:**
    - Crear endpoint POST /pedidos/prioridad donde recibe el PrioridadRequest y retorna PedidoResponse actualizado para guardarlo en el estado global
- **Pruebas Unitarias:**
    - Validación de que se tenga que elegir obligatoriamente una de las prioridades
    - Crear pruebas unitarias para alcanzar cobertura



## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
