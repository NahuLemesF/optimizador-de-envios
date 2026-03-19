# Subtasks

## HU-01 | Registrar pedido de envío

## HU-02 | Definir prioridad del envío

### Objetivo de la historia:
Permitir al usuario seleccionar el criterio de optimización del envío para el sistema guarde su preferencia y usarla en el cálculo de la recomendación

### Subtareas DEV

#### Backend
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

#### Frontend

- **Vista/UI:**
    - Crear pantalla de selección de prioridad con las opciones de “ECONOMICO, RAPIDO”
- **Lógica del cliente:**
    - Validar que el usuario tenga que seleccionar una opción
    - Guardar la prioridad en el estado global
    - Manejar errores que envíe el backend
- **Pruebas Unitarias:**
    - Selección de prioridad y validar que sea obligatoria
    - Pruebas de cobertura

### Subtareas QA

#### Análisis funcional
- Revisar que la HU, las reglas de negocio y los criterios de aceptación sean claros, consistentes y testeables.
- Validar que el flujo de registro del pedido esté alineado con el PRD y el alcance del MVP.
- Verificar la coherencia entre origen, destino, peso, unidad de peso, peso normalizado y distancia.

#### Diseño de casos de prueba
- Diseñar casos de prueba para registro exitoso de pedido con datos válidos.
- Diseñar casos de prueba para campos obligatorios vacíos o incompletos.
- Diseñar casos de prueba para peso fuera de rango:
  - menor a 0.001 Kg
  - mayor a 70 Kg
- Diseñar casos de prueba para origen y destino dentro de Colombia.
- Diseñar casos de prueba para intento de selección de ubicaciones fuera de Colombia.
- Diseñar casos de prueba para cálculo de distancia entre origen y destino.

---

## HU-03 | Obtener recomendación principal de proveedor de envío

## HU-04 | Obtener opciones alternativas de proveedores

## HU-05 | Seleccionar y confirmar proveedor
