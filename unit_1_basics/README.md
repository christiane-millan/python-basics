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

* Suma: `+`
* Resta: `-`
* Multiplicación: `*`
* División: `/` y `//`
* Exponente: `**`

[**`Ejemplo 2`**](./ejemplo-02/operadores_aritmeticos.ipynb)

<ins>Interpolación de strings</ins>

Para mejorar la intepretación de las salidas (outputs) de los programa. Se utiliza la interpolación de _strings_ o cadenas. 

Existen diferentes formas, pero una de las más simples y prácticas es el uso de `f-strings`.

[**`Ejemplo 3`**](./ejemplo-03/interpolacion_strings.ipynb) [**`Reto 1`**](./reto-01/interpolacion_strings.ipynb)

## Operadores lógicos y de comparación

Los operadores de comparación de Python son

* Mayor que: `>`
* Menor que: `<`
* Mayor o igual que: `>=`
* Menor o giual que: `<=`
* Igual que: `==`
* Diferente que: `!=`

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



