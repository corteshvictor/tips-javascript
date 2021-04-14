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
- Buscas la pagina web a editar.
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
	type:'car',
	[dynamic]:2021
}
console,log(vehicle) //output: { type: 'car', model: 2021 }
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
