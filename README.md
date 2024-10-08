# Tips en JavaScript

## **Índice**
 - [Formatear la salida de JSON Stringify](#formatear-la-salida-de-json-stringify)
 - [Obtener el índice de una iteración en un bucle for-of](#obtener-el-índice-de-una-iteración-en-un-bucle-for-of)
 - [Intercambiar variable](#intercambiar-variable)
 - [Ordenar arreglos](#ordenar-arreglos)
 - [Edita páginas web directamente en el navegador sin tocar los elementos HTML](#edita-páginas-web-directamente-en-el-navegador-sin-tocar-los-elementos-html)
 - [Copiando objetos desde las herramientas de desarrollo o developer tools](#copiando-objetos-desde-las-herramientas-de-desarrollo-o-developer-tools)
 - [Utilizar las propiedades-métodos-eventos de un elemento HTML por medio de su id](#utilizar-las-propiedades-métodos-eventos-de-un-elemento-html-por-medio-de-su-id)
 - [Desplácese hasta un elemento específico con una animación de desplazamiento suave](#desplácese-hasta-un-elemento-específico-con-una-animación-de-desplazamiento-suave)
 - [Agregando propiedades dinámicas a un objeto](#agregando-propiedades-dinámicas-a-un-objeto)
 - [Eliminar los duplicados de un array](#eliminar-los-duplicados-de-un-array)
 - [Filtrar los valores considerados falsos](#filtrar-los-valores-considerados-falsos)
 - [Arguments en funciones tradicionales o normales](#arguments-en-funciones-tradicionales-o-normales)
 - [Actualizar el estado mediante la composición de funciones en React](#actualizar-el-estado-mediante-la-composición-de-funciones-en-react)
 - [Utilizar objetos literales en lugar de if anidados o switch](#utilizar-objetos-literales-en-lugar-de-if-anidados-o-switch)
 - [Truco Node js para utilizar cualquier puerto](#truco-node-js-para-utilizar-cualquier-puerto)

## Formatear la salida de JSON Stringify

Uso clásico de `JSON.stringify()` y el uso para dar formato `JSON.stringify(object, null, 2)`
```js
const object = {
	firstName: "firstName",
	lastName: "lastName",
	birthDate: "1986-01-01", 
	homeAddress: {
		state: "state",
        address: "Address 34 56 apt 501",
        city: "city",
        zipCode: "zipCode"
    }
}

// Uso clásico
console.log(JSON.stringify(object))

/* output
'{"firstName":"firstName","lastName":"lastName","birthDate":"1986-01-01","homeAddress":{"state":"state","address":"Address 34 56 apt 501","city":"city","zipCode":"zipCode"}}'
*/

// Pasando el número 2 como tercer parámetro o argumento permite formatear la salida con 2 espacios de sangría.
console.log(JSON.stringify(object, null, 2))

/* output
'{
  "firstName": "firstName",
  "lastName": "lastName",
  "birthDate": "1986-01-01",
  "homeAddress": {
    "state": "state",
    "address": "Address 34 56 apt 501",
    "city": "city",
    "zipCode": "zipCode"
  }
}'
*/
```

## Obtener el índice de una iteración en un bucle for-of

Un bucle for...of, introducido en ES6, es una excelente manera de iterar sobre una matriz:

```js
const arr = [ 'a', 'b', 'c' ]
for (const value of arr) {
  console.log(value)
}
```
¿Cómo se puede obtener el índice de una iteración?

El bucle no ofrece ninguna sintaxis para hacer esto, pero puede combinar la sintaxis de desestructuración introducida en ES6 con llamar al `entries()` método en el [Array.prototype.entries()](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/entries):

```js
const arr = [ 'a', 'b', 'c' ]
for (const [index, value] of arr.entries()) {
  console.log(index, value)
}
```

## Intercambiar variable
Los valores de dos variables se pueden intercambiar en una expresión de desestructuración
```js
let a = 12;
let b = 6;
[b, a] = [a, b]
console.log(a, b) //output: 6, 12
```

## Ordenar arreglos
Si intentas ordenar arreglos con el método `sort()` notaras que no da el resultado esperado.
```js
const numbers = [1, 4, 7, 2, 3, 896, 2334, 400, 100]
numbers.sort()
//output: [1, 100, 2, 2334, 3, 4, 400, 7, 896]
```
Te muestro una pequeña forma de hacerlo y esperar el resultado de la forma correcta.
```js
const numbers = [1, 4, 7, 2, 3, 896, 2334, 400, 100]
numbers.sort((a, b) => a - b)
//output: [1, 2, 3, 4, 7, 100, 400, 896, 2334]
```

## Edita páginas web directamente en el navegador sin tocar los elementos HTML
- Abres tu navegador
- Buscas la pagina web a editar.
- Ingresas a las herramientas de desarrollo (click derecho inspect o tecla F12)
- Ingresas a la pestaña Consola o Console.
- Escribes el comando para encender la edición o apagarla. `document.designMode='on'` o `document.designMode='off'`
<img width="700" alt="imagen" src="https://user-images.githubusercontent.com/17968316/114419681-41aae900-9b79-11eb-8e1a-9b2835b7f8f4.png">

## Copiando objetos desde las herramientas de desarrollo o developer tools
- Abres tu navegador
- Ingresas a las herramientas de desarrollo (click derecho inspect o tecla F12)
- Ingresas a la pestaña Consola o Console.
- Supongamos que tenemos un `console.log(object)` en nuestro código y cuando vamos a la consola lo vemos.
- Lo puedes copiar haciendo clic derecho en el objeto y copiar objeto.
<img width="315" alt="imagen" src="https://user-images.githubusercontent.com/17968316/114424611-e92a1a80-9b7d-11eb-8b61-bf6e15d83041.png">
- o puedes utilizar Store object as global variable y después el método `copy` de la siguiente forma:
<img width="315" alt="imagen" src="https://user-images.githubusercontent.com/17968316/114424848-1f679a00-9b7e-11eb-99e9-fd66b3aa1db6.png">

## Utilizar las propiedades-métodos-eventos de un elemento HTML por medio de su id

Si tienes un elemento en el DOM con un id, este se almacena en window y puedes obtener este elemento con javascript o desde la consola como se muestra en la siguiente imagen.
<img width="895" alt="imagen" src="https://user-images.githubusercontent.com/17968316/114426790-07911580-9b80-11eb-9e79-8fa683892ef4.png">
- `window.app` te devuelve el elemento html.
- `window.hi.getAttribute('for')` estas utilizando el método getAttribute para obtener el valor del atributo for del elemento `label`
- `window.hi.textContent` estas obteniendo el valor de la propiedad textContent del elemento `label`

## Desplácese hasta un elemento específico con una animación de desplazamiento suave
¿Sabías que puedes desencadenar un desplazamiento en un elemento específico utilizando una sola llamada a una función en JavaScript?

Incluso puedes añadir un comportamiento para conseguir una bonita animación de desplazamiento suave.
```js
const element = document.getElementById('elementId')

element.scrollIntoView({
	behavior:  "smooth"
});
```
**Nota:** En IE11 no funciona.

## Agregando propiedades dinámicas a un objeto
```js
const dynamic = 'model'
const vehicle = {
	type: 'car',
	[dynamic]: 2021
}

console.log(vehicle) //output: { type: 'car', model: 2021 }
```
## Eliminar los duplicados de un array
Utilizando Set y spread operator
```js
const arr = [ 'Victor', 'Cortes', 'Victor', 'Hugo' ]
const uniqueArr = [ ... new Set(arr) ]
console.log(uniqueArr) //output: [ 'Victor', 'Cortes', 'Hugo' ]
```

## Filtrar los valores considerados falsos
```js
const arr = [ 0, 'Valores', false, null, 'Verdaderos', undefined, true, 3 ]
const filtered = arr.filter(Boolean)
console.log(filtered) //output: [ 'Valores', 'Verdaderos', true, 3 ]
```

## Arguments en funciones tradicionales o normales
Cuando utilizas una función tradicional o normal, estas tienen incluido un objeto arguments que es similar a un arreglo y digo similar porque tiene un índice numerado y la propiedad `length`, pero en verdad no es un arreglo porque no posee todos los métodos de manipulación de los arreglos.

Esto puede ser muy útil, porque puedes llamar a la función pasándole más parámetros de los que formalmente declaraste o de pronto no declaraste, es decir, a simple vista la función no recibe parámetros o argumentos.

Con Spread operator `(...)` podemos copiar el contenido del objeto arguments a una variable y esta nueva variable ya puede ser manipulada.

```js
function getArguments() {
  console.log(arguments) //output mas abajo
  const array = [...arguments]
  console.log(array). //output: [ 'V', 'H', 'C' ]
}

getArguments('V','H','C')

/* Output: del console.log(arguments)
{
  '0': 'V',
  '1': 'H',
  '2': 'C',
  length: 3,
  callee: ƒ getArguments(),
  __proto__: {...}
}
*/
```
**Nota:** Esta es una de las tantas principales diferencias entre una arrow functions y una función normal, las arrow functions no tienen arguments.

## Actualizar el estado mediante la composición de funciones en React
Si utilizas composición de funciones, te pueden ser muy útiles para diferentes propósitos.
En el siguiente ejemplo: se compone una función para crear diferentes funciones de [setter](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/set) para actualizar el estado.

```js
import { useState } from "react";

export default function App() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");

  //Set State using function composition
  const setState = (set) => (event) => set(event.target.value);

  const handleSubmit = (event) => {
    event.preventDefault();
    console.log(firstName, lastName);
    setFirstName("");
    setLastName("");
  };

  return (
    <div className="App">
      <h2>Enter user data</h2>
      <form onSubmit={handleSubmit}>
        <label htmlFor="first-name">firstName:</label>
        <input
          id="last-name"
          value={firstName}
          onChange={setState(setFirstName)}
        />

        <label htmlFor="last-name">lastName:</label>
        <input
          id="last-name"
          value={lastName}
          onChange={setState(setLastName)}
        />

        <button disabled={!firstName || !lastName}>add</button>
      </form>
    </div>
  );
}
```

## Utilizar objetos literales en lugar de if anidados o switch
En JavaScript estamos acostumbrados a utilizar objetos para casi todo, entonces cuando hay varias condiciones, pienso que los objetos literales son la forma más legible de estructurar el código.

Imaginemos que tenemos una función que te devuelve una frase dependiendo del tiempo atmosférico. 
**Nota**: Para nuestro ejemplo quiero utilizar mayúsculas (`.toUpperCase()`) para resaltar el clima, pero se puede utilizar minúsculas (`.toLowerCase()`).

Si utilizamos la sentencia `if/else`, se vería algo como esto:

```js
function setWeather(climate) {
  const weather = climate.toUpperCase();
  if (weather === 'SUNNY') {
    return 'It is nice and sunny outside today';
  } else if (weather === 'RAINY') {
    return `It's raining heavily`;
  } else if (weather === 'SNOWING') {
    return 'The snow is coming down, it is freezing!';
  } else if (weather === 'OVERCAST') {
    return `It isn't raining, but the sky is grey and gloomy`;
  } else {
    return 'Weather not found!';
  }
}
```
Definitivamente creo que no es algo muy legible, por ende, pensamos utilizar `switch` para mejorar:

```js
function setWeather(weather) {
  switch (weather.toUpperCase()) {
    case 'SUNNY':
    return 'It is nice and sunny outside today';
    case 'RAINY':
    return `It's raining heavily`;
    case 'SNOWING':
    return 'The snow is coming down, it is freezing!';
    case 'OVERCAST':
    return `It isn't raining, but the sky is grey and gloomy`;
    default:
    return 'Weather not found!';
  }
}
```
Ya comienza a verse un poco mejor, pero se puede presentar un inconveniente, por ejemplo si nos olvidamos de colocar el `break` o `return` dependiendo el caso, seguirá ejecutando las lineas siguientes de código y esto puede ser un problema. Entonces dicho esto, es posible que sea mucho mejor utilizar objetos literales ya que se vería de la siguiente forma:

```js
function setWeather(weather) {
  const atmosphericWeather = {
    SUNNY: 'It is nice and sunny outside today',
    RAINY: `It's raining heavily`,
    SNOWING: 'The snow is coming down, it is freezing!',
    OVERCAST: `It isn't raining, but the sky is grey and gloomy`,
    default: 'Wather not found!'
  }
 
  return atmosphericWeather[weather.toUpperCase()] || atmosphericWeather['default'];
}
```
o puedes utilizar [nullish coalescing](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator) para asignar una respuesta predeterminada:

```js
function setWeather(weather) {
  const atmosphericWeather = {
    SUNNY: 'It is nice and sunny outside today',
    RAINY: `It's raining heavily`,
    SNOWING: 'The snow is coming down, it is freezing!',
    OVERCAST: `It isn't raining, but the sky is grey and gloomy`
  }
  
  return atmosphericWeather[weather.toUpperCase()] ?? 'Weather not found!';
}
```

## Truco Node js para utilizar cualquier puerto

Cuando habilitas un servidor en Node.js, para entorno de desarrollo, puedes pasar el 0 como puerto, Node busca un puerto libre.

```javascript
const { PORT = 0 } = process.env

server.listen(0, function () {
	console.log('Este es un puerto libre de forma aleatoria: ', this.address().port);
	console.log(`server running on: http://localhost:${this.address().port}`)
}
```

