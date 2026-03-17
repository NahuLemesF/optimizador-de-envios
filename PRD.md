# Producto: Optimizador de envíos


## Visión
Construir una herramienta logística que automatice la selección del proveedor de envíos más conveniente, ayudando a las empresas que realizan envíos a reducir costos operativos y mejorar las condiciones de precio y tiempo de entrega para el cliente final.

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
  Si el algoritmo calcula mal el cruce entre peso y distancia al destino, podría asignar sistemáticamente la opción más cara cuando el usuario prioriza el costo.

- **Incumplimiento de la propuesta de valor:**  
  Si el usuario prioriza “más rápido” y el sistema falla en estimar los tiempos, el producto puede llegar tarde, afectando la reputación del negocio.

- **Incompatibilidad del modelo del “Proveedor local”:**  
  Empresas como DHL y FedEx tienen sistemas y matrices de precios estandarizados y muy estructurados. Un proveedor local en cambio, puede ser más informal, y el sistema correría riesgos tales como:
  - Cambios de precio sin aviso  
  - Información desactualizada  

### Tecnico

- **Si adaptamos el negocio acoplado fuertemente solo a DHL, FedEx o local**, va a complicar la escalabilidad si quiero por ejemplo agregar un nuevo proveedor.

- **Inconsistencia en los datos de entrada:**  
 Existe riesgo de fallos si el sistema no gestiona los tipos de datos de forma adecuada (ej. tipos de medidas en peso y distancia, tipo de moneda).


- **Manejo de casos límite:**  
El sistema debe manejar casos límite como por ejemplo el considerar destinos en donde los proveedores no tengan cobertura.
