# Producto: Optimizador de envíos

## Introducción:
A la hora de realizar el envío de un producto, las empresas/personas pueden encontrarse con el problema de no saber qué proveedor logístico elegir.
Esto puede resultar problemático ya que una selección inadecuada puede generar mayores costos de envío o tiempos de entrega que no cumplan con lo esperado por el cliente final.
El Optimizador de Envíos propone una solución que resuelve este conflicto de forma rápida, automatizada y eficiente, brindando al cliente la posibilidad de elegir si desea priorizar menor costo o mayor velocidad.

---

## Visión
Construir una herramienta logística que automatice la selección del proveedor de envíos más conveniente, ayudando a mejorar las condiciones de precio y tiempo de entrega para el cliente final.

---

## Objetivos
- **Automatizar** la selección del proveedor de transporte evaluando las opciones entre **FedEx, DHL y proveedores locales**.  
- **Centralizar** múltiples proveedores de transporte en una sola herramienta **simplificando** el proceso de toma de decisiones.  
- Permitir la **optimización** del envío según la prioridad elegida por el cliente:  
  - Menor costo  
  - Menor tiempo de entrega  
- Unificar y proveer estimaciones de precio y tiempo de entrega para entregar al cliente la opción más adecuada a sus requerimientos.

---

## Reglas de Negocio Generales

- **Regla 1:** El sistema **solo debe operar** para envíos dentro de **Colombia**.
- **Regla 2:** Para calcular una cotización, el usuario debe ingresar **obligatoriamente origen, destino y peso del paquete**.
- **Regla 3:** El sistema no debe permitir calcular opciones si el paquete supera los límites admitidos por los proveedores disponibles; **el peso debe ser mayor o igual a 0,001 Kg y menor o igual a 70 Kg**.
- **Regla 4:** El usuario debe seleccionar una prioridad de envío (menor costo o menor tiempo) para que el sistema pueda generar la recomendación.
- **Regla 5:** Si la **prioridad es menor costo**, el **sistema** debe **recomendar la opción de menor costo** disponible.
- **Regla 6:** Si la **prioridad es menor tiempo de entrega**, el sistema **debe recomendar la opción de menor tiempo** disponible.
- **Regla 7:** Si **existe empate en el menor costo**, el sistema debe **recomendar la opción con menor tiempo de entrega** entre las empatadas.
- **Regla 8:** Si **existe empate en el menor tiempo de entrega**, el sistema debe **recomendar la opción con menor costo** entre las empatadas.
- **Regla 9:** El sistema debe **mostrar opciones alternativas** distintas a la recomendación principal para permitir la comparación si se da el caso.
- **Regla 10:** El usuario debe **seleccionar un proveedor** para poder continuar con el proceso del pedido.


## Alcance del MVP

### In
- **Registro de datos del envío:** el sistema permite ingresar origen, destino y peso del pedido.
- **Selector de prioridad del envío**: el sistema permite elegir si se desea priorizar **menor costo** o **menor tiempo de entrega**.
- **Motor de evaluación centralizado:** el sistema compara las opciones de transporte disponibles (*FedEx*, *DHL* y *proveedores locales*) y evalúa considerando costo y tiempo estimado.
- **Generación de recomendación principal:** el sistema devuelve la opción más adecuada según la prioridad seleccionada por el usuario.
- **Visualización de opciones alternativas:** el sistema muestra otras opciones disponibles para que el usuario pueda compararlas con la recomendación principal.
- **Selección de proveedor:** el usuario puede elegir una de las opciones disponibles para continuar con el proceso del pedido.

### Out
- **Gestión de usuarios y perfiles.**
- **Integración en tiempo real con APIs de proveedores logísticos.**
- **Módulo de pagos.**
- **Seguimiento del envío (tracking).**
- **Gestión de pedidos internacionales.**

---

## Riesgos de negocio y técnicos

### Negocio

- **Pérdidas financieras por fallos de lógica:**  
  Si el algoritmo calcula mal el cruce entre peso y distancia desde el origen al destino, podría asignar sistemáticamente la opción más cara cuando el usuario prioriza el costo.

- **Incumplimiento de la propuesta de valor:**  
  Si el usuario prioriza “más rápido” y el sistema falla en estimar los tiempos, el producto puede llegar tarde, afectando la experiencia de usuario del cliente.

- **Incompatibilidad del modelo del “Proveedor local”:**  
  Empresas como DHL y FedEx tienen sistemas y matrices de precios estandarizados y muy estructurados. Un proveedor local en cambio, puede ser más informal, y el sistema correría riesgos tales como:
  - Cambios de precio sin aviso  
  - Información desactualizada  

### Técnico

- **Acoplamiento fuerte a proveedores específicos:** una implementación poco flexible puede dificultar la escalabilidad (ejemplo: agregar un nuevo proveedor) en futuras versiones.

- **Inconsistencia en los datos de entrada:** si el sistema no gestiona los tipos de datos de forma adecuada (ejemplo: tipos de medidas en peso, origen y destino correctos, tipo de moneda) podría verse afectado el cálculo de las opciones disponibles.

- **Manejo insuficiente de casos límite:** destinos sin cobertura o pesos no admitidos por los proveedores pueden generar fallos si no se controlan adecuadamente.

