# Funciones

Las funciones son bloques de código nombradas que son diseñadas para realizar un trabajo específico. Cuando se realizar una tarea en partícular que se ha definido en una función, se realiza la _llamada_ de la función a través de su nombre. Si es necesario realizar la tarea múltiples veces en varias secciones del programa, de esta forma no es necesario escribir el código para la misma tarea en diferentes secciones.

````python
"""
Definición de la función """

def greet_user(username):
    """Display a simple greeting."""
    print("Hello, " + username.title() + "!")


"""
Llamada a la función. """
greet_user('jesse')
````

Características de una función
* Tiene un nombre
* Piensa en una variable que está vinculada a un objeto función.
* Tiene parámetros (formales) (0 o más)
* Es decir, los valores de entrada.
* Tiene una docstring (opcional, pero recomendada)
* Es un comentario delimitado por comillas triples (""") que proporciona una especificación de la función — un contrato que relaciona la entrada con la salida.
* Tiene un cuerpo, es decir, un conjunto de instrucciones que se ejecutan cuando se llama a la función.
* Devuelve algo
* Utiliza la palabra clave return.
__Argumentos y parámetros__

En el ejemplo anterior la variable `username` de la definición de la función `greet_user()` es un ejemplo de un __parámetro__, una pieza de información que la función necesita para realizar su trabajo. El valor `'jesse'` es un ejemplo de un __argumento__. Un argumento es una pieza de información que pasa de una _llamada de la función_ a la función.

- [**`Ejemplo 12 - Funciones`**](./ex-functions.ipynb)

>🏋️ __Práctica funciones: División__
>
> Objetivo: Comprender el uso de parámetros, el cuerpo de una función, el operador módulo (%) y el uso del valor de retorno (return) para resolver un problema simple con funciones.
>
> __Instrucciones:__
>
> 1. Define una función llamada div_by(n, d) que reciba dos números enteros positivos.
> 2.	La función debe:
> 
> * Verificar si d divide a n exactamente (es decir, sin residuo).
> * Retornar True si lo divide, o False en caso contrario.
> 3.	Agrega una docstring que documente el comportamiento de la función.
> 4.	Prueba tu función con los siguientes pares de valores:
> * n = 10 y d = 3
> * n = 195 y d = 13

### Alcance de las variables de una función

```python
def operation(x):
    y = 1
    x = x + y
    print('x = ', x)
    return x

x = 3
y = 2
z = operation(x)

print('x = ', x)
print('y = ', y)
print('z = ', z)

```

## Paso de Listas a funciones

En ocasiones sera muy util realizar el paso de una lista a una función o objetos más complejos como los diccionarios. 

Cuando se pasa una lista a una función, la función accede directamente al contenido de la lista. 

Ejemplo.

````python
def greet_users(names):
    """Print a simple greeting to each user in the list."""
    for name in names:
        msg = "Hello, " + name.title() + "!"
        print(msg)

usernames = ['hannah', 'ty', 'margot'] 
greet_users(usernames)
````

147-mt

 [**`Ejemplo 13 - Funciones con Listas `**]()
  
**Modificación de una lista en una función**

Cuando se pasa una lista a una función, la función puede modificar la lista, cualquier cambio realizado a lista dentro de la función será permanente, con la finalidad de hacer eficiente el trabajo cuando se trabaja con una gran cantidad de datos.

```python
def greet_users(names):
    """Print a simple greeting to each user in the list."""
    names.append("dev")
    for name in names:
        msg = "Hello, " + name.title() + "!"
        print(msg)

usernames = ['hannah', 'ty', 'margot'] 
my_greet_users(usernames)

print(usernames)
```

**Prevenir que una función modifique una lista**

Mandar una copia de la lista

```python
function_name(list_name[:])
```

**Pasar un número arbitrario de argumentos**

```python
def make_pizza(*toppings):
    """Summarize the pizza we are about to make."""
  print("\nMaking a pizza with the following toppings:")
  for topping in toppings:
        print("- " + topping)

make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```

El asterisco indica a Python la creación de una tupla que empaca cualquier valor recibido.

**Mezcla de argumentos posicionales y arbitrarios**

El argumento arbitrario debe ser colocada al final de la lista de parámetros en la definición de la función. Es decir, los argumentos posicionales y de palabra clave deben ir primero.

```python
def make_pizza(size, *toppings):
    """Summarize the pizza we are about to make."""
    print("\nMaking a " + str(size) +
          "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

**Uso de argumentos arbitrarios de palabras clave**

Si desea aceptar un número arbitrario de argumentos, pero no se sabe que tipo de información se recibirá, se puede utilizar pares de claves-valor.

```python
def build_profile(first, last, **user_info):
    """Build a dictionary containing everything we know about a user."""
    profile = {}
    profile['first_name'] = first
    profile['last_name'] = last
    for key, value in user_info.items():
        profile[key] = value
    return profile
user_profile = build_profile('albert', 'einstein',
                             location='princeton',
                             field='physics')
print(user_profile)
```

El doble asterisco en el parámetro de la definición de la función crea un diccionario.

# Módulos

Crear módulo `pizza.py`

```python
def make_pizza(size, *toppings):
    """Summarize the pizza we are about to make."""
    print("\nMaking a " + str(size) +
        "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)
```

**Importar un módulo completo**

```python
import pizza
```

**Importar una función en específico**

```python
from pizza import make_pizza
```

**Uso de un alias para una función**

```python
from pizza import make_pizza as mp
```

**Uso de un alias para un módulo**

```python
import pizza as p
```

**Importar todas las funciones de un módulo**

```python
from pizza import *
```

>🏋️ __Práctica funciones: Uso de módulos e importaciones en Python__
>
> Objetivo: Aprender a organizar el código en módulos y utilizar distintas formas de importación para estructurar programas más limpios, escalables y reutilizables.
>
> __Instrucciones:__
>
> 1. Crea una carpeta llamada `calculadora/`.
> 2. Dentro de esa carpeta, crea tres archivos Python:
> 3. Archivo `aritmetica.py`, define las funciones sumar y restar para dos números
> 4. Archivo `multiplicacion_division.py`, define las funciones multiplicar y dividir para dos números.
> 5. Archivo `main.py`.
> 
> Este será el programa principal. Aquí deberás:
> 
> * Importar funciones de los otros dos archivos utilizando:
> 
>   * `import aritmetica`
>	* `from multiplicacion_division import multiplicar`
>	* `import multiplicacion_division as md` (para acceder a dividir)
>* Solicitar dos números al usuario y mostrar el resultado de las cuatro operaciones usando las funciones importadas.
>* Agrega impresión formateada con __f-strings__.


# Type hits

```python
def greet(name: str) -> str:
    return "Hello, " + name
```

```python
def headline(text: str, align: bool = True) -> str:
	if align:
		return f"{text.title()}\n{'-' * len(text)}"
	else:
		return f" {text.title()} ".center(50, "o")
```

```python
>>> print(headline("python type checking"))
Python Type Checking
--------------------

>>> print(headline("python type checking", align=False))
oooooooooooooo Python Type Checking oooooooooooooo
```

# Type Checking

Es necesario instalar `Mypy` en el ambiente virtual

```python
def headline(text: str, align: bool = True) -> str:
	if align:
		return f"{text.title()}\n{'-' * len(text)}"
	else:
		return f" {text.title()} ".center(50, "o")

print(headline("python type checking"))
print(headline("python type checking", align="center"))
```

Ejecutar

```python
mypy headlines.py

```

**Ventas y desventajas de Type Hits**

- Ayuda a identificar ciertos errores
- Ayuda a documentar el código
- Permite construir y mantener una arquitectura limpia

Sin embargo el tipado estático tiene algunas desventajas:

- Toma tiempo y esfuerzo
- Es mejor en versiones recientes de Python
- Reduce ligeramente el tiempo de ejecución

>🏋️ __Práctica funciones: Type Hints y verificación con mypy__
>
> Objetivo: Aprender a utilizar anotaciones de tipo en funciones de Python y validar que el código cumple con las expectativas de tipo mediante la herramienta mypy.
>
> __Instrucciones:__
>
> 1.	Escribe las siguientes funciones en un archivo llamado operaciones.py, agregando las anotaciones de tipo correspondientes:
>
> ```python
> def suma(a, b):
>     return a + b
> 
> def longitud(texto):
>     return len(texto)
> 
> def es_par(numero):
>     return numero % 2 == 0
> 
> def repetir_texto(texto, veces):
>     return texto * veces
> ```
>
> 2. Agrega anotaciones de tipo (type hints) en cada función, especificando el tipo de los parámetros y del valor de retorno.
>
> 3. Instala mypy y verifica tu código usando mypy


# Anotations

En las funciones, se puede anotar los argumentos y los valores de retorno.

```python
import math

def circumference(radius: float) -> float:
	return 2 * math.pi * radius
```

```python
>>> circumference.__annotations__
{'radius': <class 'float'>, 'return': <class 'float'>}
>>> circumference(1.23)
7.728317927830891
```

reveal.py

```python
import math
reveal_type(math.pi)

radius = 1
circumference = 2 * math.pi * radius
reveal_locals()
```

Ejecución

```python
❯ mypy reveal.py
reveal.py:2: note: Revealed type is "builtins.float"
reveal.py:6: note: Revealed local types are:
reveal.py:6: note:     circumference: builtins.float
reveal.py:6: note:     radius: builtins.int
Success: no issues found in 1 source file
```

```python
❯ python3 reveal.py
Traceback (most recent call last):
  File "reveal.py", line 2, in <module>
    reveal_type(math.pi)
NameError: name 'reveal_type' is not defined
```

Anotaciones en variables

```python
>>> pi: float = 3.142
>>> def circumference(radius: float) -> float:
>>>     return 2 * pi * radius

>>> circumference.__annotations__
{'radius': <class 'float'>, 'return': <class 'float'>}

>>> __annotations__
{'pi': <class 'float'>}

>>> circumference(1)
6.284
>>> nothing: str

>>> nothing
Traceback (most recent call last):
  File "<input>", line 1, in <module>
    nothing
NameError: name 'nothing' is not defined
>>> __annotations__
{'pi': <class 'float'>, 'nothing':<class 'str'>}
```
