# FUNCIONES Y SCOPE

## OBJETIVO 

> Leer el código javascript de  y aprender a identificar las funciones globales, locales, funciones de callback, expresions, statement, clousure, scope, contextos de ejecucion, que funciones forman parte de la pila de ejecucion (stack execution) y que funciones forman parte de la cola de eventos (event queue) y de esta manera poder enriquecer nuestro léxico técnico como frontend.

## FUNCIONES GLOBALES
* Son las funciones que *no se encuentran dentro de otra funcion*:
> $(document).ready(function()

## F. LOCALES
* Son las funciones que *si se encuentran dentro de otra funcion*:
> * $inputCard.on('input', function()
> * function activeButton() 
> * function desactiveButton()
> * function longitud(input)
> * function soloNumeros(input)
> * function isValidCreditCard(numberCard)

## F. DE CALLBACK
* Cuando invoco una función pasándole como parámetro otra función
> function isValidCreditCard(numberCard) {

## F. EXPRESIONS
* Cuando invoco a la funcion despues de crearla.
> Invoco a las funciones:
 activeButton();
desactiveButton();
desactiveButton();
soloNumeros(input), Despues de crearlas.

## F. STATEMENT
* Cuando invoco a la funcion antes de crearla
> En la linea (15) llamo a la funcion *isValidCreditCard($(this).val().trim())* Cuando aun se crea en la linea 44.

## CLOUSURE
* Es la habilidad que tienen las funciones para recordar el contexto en que fueron creadas, incluso cuando se les invoca en un contexto diferente.

> Por ejemplo, La función *$inputCard.on('input', function()*, fue creada en el scope de la función *$(document).ready()*,pero invoca a la funcion *isValidCreditCard* que recien es creada en la linea 44 y gracias al closure  puede utilizarla.

> Otro ejemplo es que en la funcion *activeButton()*   utilizan la variable  *$buttonNext*, que es creada en el mismo contexto que ellas de la función *$(document).ready()*.

> La función *$(document).ready(function()*, crea una variable local llamada *$inputCard*, a continuación, define una función denominada *$inputCard.on('input', function()*, es una función interna (un closure) definida dentro de otra funcion, y sólo está disponible en el cuerpo de esa función, no tiene ninguna variable propia, lo que hace es reutilizar la variable $inputCard declarada en la función externa.

## SCOPE
* El scope es el alcance de una variable, puede ser de dos tipos, global y local. Una variable cuyo scope es global se puede acceder desde cualquier parte del código, una local solo desde la función que la contiene. Ejemplo:
> var $inputCard , var $inputMonth, var $inputYear, var $buttonNext, var regexOnlyNumbers, var labelErrorOrSuccessMessages. var arr, var sumaTotal, var index son vaariable  *LOCALES* que solo existen dentro de la funcion $(document).ready(function().

## STACK EXECUTION
* Funciones que forman parte de la pila de ejecución. 
```
 $(document).ready(function() {
   activeButton();
   desactiveButton()
   longitud(input)
   soloNumeros()
   isValidCreditCard(numberCard);
  });  
```

## EVENTO QUEUE
* Funciones que forman parte de la cola de eventos en el *contexto de ejecucion*.

>* Función isValidCreditCard()
>* Función soloNumeros()
>* Función longitud() vinculadas al evento *input*.


