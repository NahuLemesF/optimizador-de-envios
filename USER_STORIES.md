# Historias de Usuario - Optimizador de Envíos

## HU1 - Registrar Pedido

### Descripción

**Como** usuario del sistema  
**quiero** registrar un pedido  
**para** poder hacer el proceso del cálculo del envío.

### Valor de Negocio
- Permite registrar un pedido con los datos necesarios para calcular el envío.
- Asegura que el sistema tenga la información correcta para generar recomendaciones de envío.
- Facilita la validación de datos de entrada para evitar errores en el proceso de cálculo.

### Definition of Ready (DoR)

- La historia de usuario está redactada de forma clara.
- Están definidos los datos de usuario para registrar el pedido: origen, peso y destino
- Las reglas de negocio sobre cobertura y peso permitido están claras.
- Los criterios de aceptación están definidos.
- La historia está revisada por DEV y QA.
- La historia puede ser estimada por el equipo técnico.

### Criterios de Aceptación

```gherkin
Escenario: Ingreso de Datos Válidos
    Dado que el usuario necesita enviar un producto
    Cuando ingresa un origen, un destino y un peso válidos
    Entonces el sistema debe registrar los datos del pedido
    Y debe permitir continuar con el cálculo del envío
```

```gherkin
Escenario: Destino sin Cobertura
    Dado que el usuario necesita enviar un producto
    Cuando ingresa un destino fuera de la cobertura de los proveedores logísticos
    Entonces el sistema no debe permitir continuar con el cálculo del envío
    Y debe informar que no hay proveedores disponibles para ese destino
```

```gherkin
Escenario: Peso no permitido
    Dado que el usuario necesita enviar un producto
    Cuando ingresa un peso mayor al permitido por los proveedores logísticos
    Entonces el sistema no debe permitir continuar con el cálculo del envío
    Y debe informar que el peso ingresado no está cubierto por los proveedores disponibles
```

### Definition of Done (DoD)
- La funcionalidad de registro de pedido está implementada.
- El sistema permite registrar origen, destino y peso válidos.
- El sistema bloquea destinos sin cobertura.
- El sistema bloquea pesos no permitidos.
- Se cumplen los criterios de aceptación definidos.
- La historia fue validada por QA.

---

## HU2 - Definir prioridad del envío

**Como** usuario del sistema  
**quiero** seleccionar si prefiero un envío económico o más rápido  
**para** poder hacer el proceso del cálculo del envío.

### Criterios de Aceptación

```gherkin
Escenario: Selección de prioridad por menor costo
    Dado que el usuario registró un pedido válido
    Cuando selecciona prioridad de menor costo
    Entonces el sistema debe utilizar el costo como criterio principal para generar la recomendación
```

```gherkin
Escenario: Selección de prioridad por menor tiempo de entrega
    Dado que el usuario registró un pedido válido
    Cuando selecciona prioridad de menor tiempo de entrega
    Entonces el sistema debe utilizar el tiempo de entrega como criterio para generar la recomendación
```

---

## HU3 - Obtener recomendación principal

**Como** usuario del sistema  
**Quiero** que el sistema me recomiende la mejor opción de envío  
**Para** elegir una alternativa que cumpla con mis necesidades

### Criterios de Aceptación

```gherkin
Escenario: Recomendación principal según prioridad de menor costo
    Dado que el usuario definió la prioridad de menor costo
    Cuando el sistema calcula las opciones disponibles
    Entonces el sistema debe devolver la opción recomendada
    Y la opción recomendada debe corresponder a la opción de menor costo disponible
```

```gherkin
Escenario: Recomendación principal según prioridad de menor tiempo
    Dado que el usuario definió la prioridad de menor tiempo
    Cuando el sistema calcula las opciones disponibles
    Entonces el sistema debe devolver la opción recomendada
    Y la opción recomendada debe corresponder a la opción de menor tiempo disponible
```

```gherkin
Escenario: Recomendación principal con empate en menor costo
    Dado que el usuario definió la prioridad de menor costo
    Y existen múltiples opciones con el mismo menor costo disponible
    Cuando el sistema calcula las opciones disponibles
    Entonces el sistema debe devolver una opción recomendada
    Y la opción recomendada debe corresponder a la de menor tiempo de entrega
```

```gherkin
Escenario: Recomendación principal con empate en menor tiempo
    Dado que el usuario definió la prioridad de menor tiempo
    Y existen múltiples opciones con el mismo menor tiempo disponible
    Cuando el sistema calcula las opciones disponibles
    Entonces el sistema debe devolver una opción recomendada
    Y la opción recomendada debe corresponder a la de menor costo
```

---

## HU4 - Consultar opciones alternativas

**Como** usuario del sistema  
**Quiero** ver otras opciones disponibles  
**Para** compararlas con la recomendación principal y evaluar la opción más conveniente.

### Criterios de aceptación

```gherkin
Escenario: Visualización de alternativas
    Dado que el sistema generó una recomendación principal
    Y existen otras opciones de envío disponibles 
    Cuando el sistema muestra la recomendación principal
    Entonces el sistema debe mostrar automáticamente las opciones alternativas disponibles
```

```gherkin
Escenario: Ausencia de opciones alternativas
    Dado que el sistema generó una recomendación principal
    Y no existen otras opciones de envío disponibles
    Cuando el sistema muestra la recomendación principal
    Entonces el sistema debe notificar que no existen otras opciones alternativas
```


---

## HU5 - Seleccionar y confirmar proveedor

**Como** usuario del sistema  
**Quiero** seleccionar el proveedor deseado  
**Para** continuar con el proceso del pedido

### Criterios de aceptación

```gherkin
Escenario: Camino Feliz - Selección del proveedor deseado
	Dado que el sistema mostró la opción recomendada y las opciones disponibles
	Cuando el usuario seleccione el proveedor deseado
	Entonces el sistema debe continuar con el proceso de pedido
```

```gherkin
Escenario: Usuario no selecciona proveedor
	Dado que el sistema mostró la opción recomendada y las opciones disponibles
	Cuando el usuario intenta continuar sin seleccionar un proveedor
	Entonces el sistema no debe continuar con el proceso de pedido
	Y debe informar que se debe seleccionar un proveedor para continuar 
```

