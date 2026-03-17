# Historias de Usuario Proyecto - Optimizacion de Envios

## HU1 - Registrar Pedido
- **Como** usuario del sistema
- **quiero** registrar un pedido 
- **para** poder hacer el proceso del cálculo del envío.

### Criterios de Aceptación:

#### Escenario 1: Camino Feliz - Ingreso de Datos Válidos
**Dado** que el usuario necesita enviar un producto
**Cuando** ingresa un origen, un destino y un peso válidos
**Entonces** el sistema debe registrar los datos del pedido
**Y** debe permitir continuar con el cálculo del envío

#### Escenario 2: Destino sin Cobertura
**Dado** que el usuario necesita enviar un producto
**Cuando** ingresa un destino fuera de la cobertura de los proveedores logísticos
**Entonces** el sistema no debe permitir continuar con el cálculo del envío
**Y** debe informar que no hay proveedores disponibles para ese destino

## HU2 - Definir prioridad del envió
- **Como** usuario del sistema
- **quiero** seleccionar si prefiero un envío económico o más rápido 
- **para** poder hacer el proceso del cálculo del envío.

## HU3 - Obtener recomendación principal
- **Como** usuario del sistema
- **Quiero** que el sistema me recomiende la mejor opción de envío
- **Para** elegir una alternativa que cumpla con mis necesidades

## HU4 - Consultar opciones alternativas
- **Como** usuario del sistema
- **Quiero** ver otras opciones disponibles
- **Para** compararlas con la recomendación principal y evaluar la opción más conveniente.

## HU5 - Seleccionar y confirmar proveedor
- **Como** usuario del sistema
- **Quiero** seleccionar el proveedor deseado
- **Para** continuar con el proceso del pedido