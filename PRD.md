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

