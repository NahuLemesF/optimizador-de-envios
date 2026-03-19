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

### Descripcion

**Como** usuario del sistema  
**Quiero** seleccionar si prefiero un envío económico o más rápido  
**Para** poder hacer el proceso del cálculo del envío.

### Valor de Negocio
- Permite seleccionar la opción de envío que es de interés para el usuario de acuerdo a sus necesidades
- Asegura que el sistema tenga la información correcta para generar recomendaciones de envío.

### Reglas Relacionadas

### Definition of Ready (DoR)

- La historia de usuario está redactada de forma clara.
- Están definidas las opciones de envio que se tendran en cuenta; economico o rapido
- Los criterios de aceptación están definidos.
- La historia está revisada por DEV y QA.
- La historia puede ser estimada por el equipo técnico.

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

### Definition of Done (DoD)
- La funcionalidad de elegir entre los dos tipos de envio esta implementada
- El sistema permite elegir entre envio con opcion economica o rapida
- El sistema no permite hacer el calculo para la recomendacion sin antes haber elegido una de las opciones de envio
- Se cumplen los criterios de aceptacion definidos
- La historia fue validada por QA

---

## HU3 - Obtener recomendación principal

### Descripción

**Como** usuario del sistema  
**Quiero** que el sistema me recomiende la mejor opción de envío  
**Para** elegir una alternativa que cumpla con mis necesidades

### Valor de Negocio
- Proporciona una recomendación personalizada basada en las preferencias del usuario.
- Facilita la toma de decisiones al destacar la opción más relevante.
- Mejora la experiencia del usuario al ofrecer una recomendación clara y directa.

### Definition of Ready (DoR)
- La historia de usuario está redactada de forma clara.
- Estan definidas las prioridades de envío disponibles: menor costo y menor tiempo de entrega.
- Están definidas las reglas de negocio para generar la recomendación principal.
- Los criterios de aceptación están definidos.
- La historia está revisada por DEV y QA.
- La historia puede ser estimada por el equipo técnico.

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

### Definition of Done (DoD)
- La funcionalidad de generar una recomendación principal está implementada.
- El sistema devuelve la opción recomendada de acuerdo a la prioridad seleccionada por el usuario.
- El sistema maneja correctamente los casos de empate en costo o tiempo.
- Se cumplen los criterios de aceptación definidos.
- La historia fue validada por QA.

---

## HU4 - Consultar opciones alternativas

### Descripción

**Como** usuario del sistema  
**Quiero** ver otras opciones disponibles  
**Para** compararlas con la recomendación principal y evaluar la opción más conveniente.

### Valor de negocio
- Permite al usuario tener control todo el tiempo sobre la decisión de que proveedor usar.
- La herramienta le da la recomendación de acuerdo a las necesidades del cliente, pero el cliente puede ver las demas opciones
- Permite al usuario tener claridad sobre otras opciones de proveedores de acuerdo a su pedido 

### Reglas relacionadas

### Definition of Ready (DoR)
- La historia de usuario está redactada de forma clara.
- Están definidas las reglas de negocio para generar las opciones de proveedores alternativas teniendo en cuenta las opciones de economico o rapido.
- Estan definidas las reglas de negocio relacionadas con los proveedores (peso y cobertura)
- Los criterios de aceptación están definidos.
- La historia está revisada por DEV y QA.
- La historia puede ser estimada por el equipo técnico.

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

### Definition of Done (DoD)


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

