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

## Alcance del MVP

### In
- Registro de pedido:
  - Origen
  - Destino  
  - Peso  
- Selector de prioridad:
  - Optimización por costos (tarifa más baja)  
  - Optimización por velocidad (servicio más ágil)  
- Motor de evaluación centralizado:
  - Evalúa y cruza entre costo y velocidad de las empresas de transporte (FedEx, DHL, Local)  
- El sistema debe devolver el resultado de la evaluación otorgando al cliente final el proveedor más adecuado según costos y tiempo.

### Out
- Módulo de Tracking (rastreo)  
- Integración en tiempo real con APIs de FedEx, DHL, Local, etc.  
- Módulo de Pagos  
- Gestión de Usuarios y creación de perfiles  

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

- **Si adaptamos el negocio acoplado fuertemente solo a DHL, FedEx o local**, va a dificultar la escalabilidad (ejemplo: agregar un nuevo proveedor).

- **Inconsistencia en los datos de entrada:**  
 Existe riesgo de fallos si el sistema no gestiona los tipos de datos de forma adecuada (ejemplo: tipos de medidas en peso, origen y destino correctos, tipo de moneda).

- **Manejo de casos límite:**  
El sistema debe manejar casos límite como por ejemplo el considerar destinos en donde los proveedores no tengan cobertura o el peso máximo permitido por cada empresa logística.
