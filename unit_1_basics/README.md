# Fundamentos de Python

## 1. Objetivos


## Scripts y Jupyter Notebooks

* Python es un lenguaje de programación de proposito general que tiene la características de crear código fácil de leer, depurar y exteender.
* Es __open source__!!
* Es un lenguaje de programación interpretado, através de scripts, se pueden construir programas para la solución de problemas complejos.
* El uso de Jupyter Notebooks permite crear prototipos de programas para crear soluciones complejas.

## Variables 

En Python. la signación de datos a las `variables` se realiza mediante `=`.

* La sintaxis es:

```python
nombre_de_la_variable = valor
```

`valor` puede ser cualquier tipo de dato

> ⚠️ uso del modo __snake_case__ para definir el identificador de una variable.


## Tipos de datos

En Python los datos son almacenados de acuerdo a su tipo. Los tipos de datos básicos son:

* `int`: números enteros
* `float`: números de punto flotante o decimales
* `string`: secuencia de caracteres 
* `booleano`: valor lógico (true o false)

> La función `type()` permite conocer el tipo de dato de una variable.

[**`Ejemplo 1`**](./ejemplo-01/variables_tipos_datos.ipynb)

## Operadores aritméticos

Los operadores aritméticos de Python son los siguiente:

| Operador | Operación        | Ejemplo  |
|----------|------------------|----------|
| `+`      | Suma             | `5 + 5`  |
| `-`      | Resta            | `7 - 5`  |
| `*`      | Multiplicación   | `3 * 7`  |
| `/`      | División entera  | `5 / 2`  |
| `//`     | División precisa | `5 / 2`  |
| `%`      | Residuo          | `5 % 2`  |
| `**`     | Potencia         | `5 ** 3` |

> Las coversiones o casting de variables es importante para asegurar los resultos esperados.
> `int()`, `float()` y `str()` son los métodos que nos permiten converti un tipo de dato a otro, entero, flotante o cadena, respectivamente.

[**`Ejemplo 2`**](./ejemplo-02/operadores_aritmeticos.ipynb)

<ins>Interpolación de strings</ins>

Para mejorar la intepretación de las salidas (outputs) de los programa. Se utiliza la interpolación de _strings_ o cadenas. 

Existen diferentes formas, pero una de las más simples y prácticas es el uso de `f-strings`.

[**`Ejemplo 3`**](./ejemplo-03/interpolacion_strings.ipynb) [**`Reto 1`**](./reto-01/interpolacion_strings.ipynb)

## Operadores lógicos y de comparación

Los operadores de comparación de Python son

| Operador | Operacion         | Ejemplo  |
|----------|-------------------|----------|
| `==`     | Igualdad          | `5 == 7` |
| `!=`     | Desigualdad       | `5 != 7` |
| `>`      | Mayor que         | `9 > 7`  |
| `<`      | Menor que         | `7 < 9`  |
| `>=`     | Mayor o igual que | `9 >= 7` |
| `<=`     | Menor o igual que | `7 <= 9` |

[**`Ejemplo 4`**](./ejemplo-04/operadores_comparacion.ipynb) [**`Reto 2`**](./reto-02/operadores_comparación.ipynb)

## Listas

Una lista es una colección de elementos en un orden en particular. Se pueden crear listas que incluyan letras, dígitos, cadenas. Se puede colocar cualquier tipo de dato en una lista y los elementos de la lista no necesitan estar en un orden en particular.

En Python los corchetes (`[]`) indican una lista, los elementos individuales en la lista estan separados por coma. 

````python
colors = ['red', 'blue', 'white', 'yellow', 'orange']
````

Las operaciones que podemos realizar a una lista son:

__Acceso a los elementos__

````python
print(colors[0])
````
__Modificar elementos__

````python
colors[0] = 'black' 
print(colors[0]) 
````

__Agregar o insertar elementos__

````python
# método append()
colors.append('black')
print(colors)

# o método insert() 
colors.insert(0,'black')
print(colors)
````

__Eliminar un elemento__

````python
# sentencia del
del colors[0]
print(colors)

# método pop
popped_colors = colors.pop()
print(colors)
print(popped_colors)

# método remove
colors.remove('white')
print(colors)
````

[**`Ejemplo 5`**](./ejemplo-05/listas_basic.ipynb)

__Los métodos `sort()` y `reverse()`__

El método `sort()` permite ordenar de forma muy fácil una lista.

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)
```

El método `sort()` cambia de forma permanente el orden en la lista. Por defecto el orden de los elementos es alfabética. Se puede invertir el orden de la siguiente manera:

```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort(reverse=True)
print(cars)
```

__La función `sorted()`__

Para mantener el orden original de una lista, pero presentar (o imprimir) los datos ordenadis se utiliza la función `sorted()`, es decir, este devuelve una lista ordenada sin afectar la lista original.

````python
print("Here is the original list:") 
print(cars)

print("\nHere is the sorted list:") 
print(sorted(cars))

print("\nHere is the original list again:") 
print(cars)
````
__Tamaño de una lista__

La función `len()` permite conocer el tamaño de una lista.

````python
len(cars)
````

## Uso de listas

Para recorrer todos los elementos de una lista, por ejemplo para imprimir cada elemento. El uso de ciclos `for` es común para realizar esta tarea repetitiva.

__`for` sobre listas__

````python
rock_stars = ['Bowie', 'Jagger', 'Morrison', 'Osbourne']

for rock_star in rock_stars:
	print(rock_star)
````

Los __list comprehension__ son en enfoque para la generación de listas en una sola línea.

````python
squares = [value**2 for value in range(1,11)]
print(squares)
````
El uso de __slicing__ perimite trabajar con partes especificas de una lista, indicando un índice inicial y final.

````python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3])
````

[**`Ejemplo 6`**](./ejemplo-06/listas_uso.ipynb)


## Tuplas

En ocasiones es necesario crear una colección como las lista, pero que no permita realizar cambios. Las tuplas una vez inicializadas no permiten realizar cambios en los elementos, es decir, los valores son considerados __inmutables__.

````python
dimensions = (200, 50)

print(dimensions[0])
print(dimensions[1])
````

[**`Ejemplo 7`**](./ejemplo-07/tuplas-basic.ipynb)

## Estructura de control selectiva


En ocasiones en un programa es necesario examinar un conjunto de condiciones y decidir que acción tomar con base a estas condiciones.

````python
cars = ['audi', 'bmw', 'subaru', 'toyota']

for car in cars:
    if car == 'bmw':
        print(car.upper())
    else:
        print(car.title())
````

[**`Ejemplo 8`**](./ejemplo-08/if.ipynb)

## Diccionarios

Los diccionarios son un tipo de dato abstracto que permiten conectar información relacionada.

````python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0['color'])
print(alien_0['points'])
````

Agregar nuevos elementos clave-valor a un diccionario

````python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)

alien_0['x_position'] = 0 
alien_0['y_position'] = 25
print(alien_0)
````

Iniciar un diccionario vacio

````python
alien_0 = {}
   
alien_0['color'] = 'green'
alien_0['points'] = 5

print(alien_0)
````

Modificar valores en un diccionario

````python
alien_0['color'] = 'yellow'
print("The alien is now " + alien_0['color'] + ".")
````
Eliminar elementos clave-valor de un diccionario

````python
del alien_0['points'] 
print(alien_0)
````

[**`Ejemplo 9`**](./ejemplo-09/diccionarios.ipynb)

## Lista de diccionarios

````python
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}

aliens = [alien_0, alien_1, alien_2]

for alien in aliens:
    print(alien)
````

## Lista en diccionarios

````python
# Store information about a pizza being ordered.
pizza = {
       'crust': 'thick',
       'toppings': ['mushrooms', 'extra cheese'],
       }
       
# Summarize the order.
print("You ordered a " + pizza['crust'] + "-crust pizza " + "with the following toppings:")

for topping in pizza['toppings']: 
    print("\t" + topping)
````

## Diccionario en un diccionario

Es posibre anidar un diccionario dentro de otro diccionario.

````python
users = {
    'aeinstein': {
        'first': 'albert',
        'last': 'einstein',
        'location': 'princeton',
    },
    'mcurie': {
        'first': 'marie',
        'last': 'curie',
        'location': 'paris',
    },
}
````

[**`Ejemplo 10`**](./ejemplo-10/diccionarios_listas.ipynb)

## While

el ciclo `while` permite repetir un bloque de instrucciones mientras la condición sea verdad.

En una estrategia simple, se puede implementar un contador y mediante una condición, determinar el número de repeticiones del bloque de instrucciones del `while`.
````python
current_number = 1
while current_number <= 5:
    print(current_number)
    current_number += 1
````

Otra forma de controlar un ciclo `while` es a través de un centinela, en este caso cuando la condición no revela que el centinela comple un valor, entonces, se repite el bloque hasta que ocurra lo contrario.

````python
prompt = "\nTell me something, and I will repeat it back to you:" 
prompt += "\nEnter 'quit' to end the program. "

message = ""
wwhile message != 'quit':
    message = input(prompt)
    print(message)
````

En otra estrategia más, el uso de una bandera permite determinar hasta cuando repetir el ciclo `while`.

````python
prompt = "\nTell me something, and I will repeat it back to you:" 
prompt += "\nEnter 'quit' to end the program. "

active = True
while active:
    message = input(prompt)
    if message == 'quit': 
        active = False
    else: 
        print(message)
````

En el siguiente ejemplo, se utilizar una estrategia basada en el uso de la sentencia `break`, la cual interrumpe la ejecución del bloque de instrucciones del ciclo `while`.

````python
prompt = "\nPlease enter the name of a city you have visited:"
prompt += "\n(Enter 'quit' when you are finished.) "

while True:
city = input(prompt)
    if city == 'quit':
        break
    else:
        print("I'd love to go to " + city.title() + "!")
````

En adición a `break` existe la sentencia `continue`, la cual salta el resto del bloque de instrucciones, pero nuevamente valida la condición del ciclo `while`.

````python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue
    
    print(current_number)
````

[**`Ejemplo 11`**](./ejemplo-11/while_listas.ipynb)

---

[Funciones](./functions/README.md)
