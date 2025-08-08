[Programación Funcional](../README.md)> 4. Funciones

Las funciones en Python son objetos de primera clase. Esto significa que son objetos y pueden ser almacenados en variables, referenciados en listas y otros tipos de estructuras, y ser pasados como parámetros de funciones o devueltos como resultado. 

# Objetos y variables en Python

```python
a = 'apple'
b = 'pear'
```

Las variables `a` y `b` mantienen referencia a los objetos de tipo string correspondientes.

```python
a = b
```

Ahora `a` y `b` hacen referencia al mismo objeto en memoria. El objeto ‘apple’ aún reside en memoria pero ya no es posible accederlo. Python en algún momento gestionará la liberación de ese espacio de memoria.

# Almacenamiento de funciones

```python
a = 10
def square(x):
    return x*x
b = square(a)
print(b)
# 100
```

Los identificadores a, b y square son variables. En el caso de def es una manera especia de definir un objeto función y asignarlo a una variables (square en este caso). Los paréntesis indican que es un objeto invocable.

```python
print(type(square))
print(id(square))
print(str(square))
```

# Alias

Cuando dos diferentes variables refieren al mismo objeto en Python

```python
t = (10, 20, 30, 40, 50) 
u=t
print(t[2]) # 30 
print(u[2]) # 30
```

se puede definir un alias para una función

```python
def square(x):
        return x*x

sq = square

a = 3
print(sq(a)) # 9
```

Incluso, los alias pueden funcionar con función de librería

```python
pr = print
pr('This is an alias')
```

## Redefinir una función

Dado que las funciones con variables en esencia, que almacenan objetos de tipo función, se pueden reasignar en cualquier momento.

```python
def a():
	print(1)

def a():
	print(2)
```

Esto puede traer consecuencias, y es mejor evitar este tipo de casos:

```python
def a():
	print(1)

def b(): 
	a()

b() #1
    
def a():
	print(2)

b() #2
```

Después de definir una función `a()` que imprime `1`. Cuando se define la función `b()` que llama a la función `a()` para que imprima un `1`. Cuando se llama a `b()` por primera vez imprime un `1` como se esperaba.

Después se redefine `a()` para que imprima `2`. ¿Qué pasa si se llama a `b()` de nuevo?

Para la función `b()` la variable a es global. Que ahora imprime un `2` cuando sea llamada.

El riesgo en este caso es el cambio de comportamiento de la función `b()`, y lo convierte en una buena receta para bugs.

# Funciones como parámetros

Considerar la siguiente función que convierte pulgadas a centímetros

```python
def inch2cm(x):
	return x*2.54

def convert(x):
	y = inch2cm(x)
	print(x, '=>', y)

convert(3)    # 3 => 7.62
```

Si se desea generalizar esta función para convertir diferentes unidades. Existen diferentes maneras de realizarlo. Se puede remover la llamada explícita de `inch2cm()` desde la función `convert()`.  En su lugar, se pasa la función como parámetro:

```python
def convert(f, x):
	y = f(x)
	print(x, '=>', y) 

convert(inch2cm, 3) # 3 => 7.62
```

Ahora, supongamos que se desea convertir una temperatura de Celsius a Fahrenheir. Se puede escribir la función:

```python
def c2f(x):
	return x*1.8 + 32
```

Para utilizar esta conversión, se necesita pasar `c2f()` a la función `convert()`

```python
convert(c2f, 18) # 18 => 64.4
```

Ahora, se desea convertir una entero a texto: `1` se conveirte en `“one”`, `2` en `“two”` y así sucesivamente. La función `i2text()`, funcionará solo para valores del 1 al 3.

```python
def i2text(x):
	text = ['zero', 'one', 'two', 'three']
	return text[x]

convert(i2text, 2)    # 2 => two
```

## La función `sorted()`

La función `sorted()` devuelve una copia de una lista ordenada:

```python
p = [3, 7, 2, 6, 1]
q = sorted(p)

print(q) # [1, 2, 3, 6, 7]
```

La función `sorted()` utiliza las comparaciones estándar de Python para ordenar la lista, en este caso ordena los números en orden incremental. Si la lista contiene cadenas, serán ordenadas de manera alfabética. 

```python
p = ['red', 'green', 'blue', 'yellow', 'cyan']
q = sorted(p)
print(q) # ['blue', 'cyan', 'green', 'red', 'yellow']
```

¿Qué pasa si se desea ordenar las cadenas de forma distinta? Por ejemplo, se desea ordenar las claves en por su tamaño de forma ascendente. Afortunadamente, la función `sorted()` tomo un parámetro opcional `key` para definir el orden.

El parámetro `key` acepta un objeto función como valor. La función es aplicada a cada elemento de la lista, y la lista es ordenada de acuerdo con el valor retornado.

Si queremos un orden de acuerdo a su tamaño:

```python
p = ['red', 'green', 'blue', 'yellow', 'cyan']
q = sorted(p, key=len)
print(q) # ['red', 'blue', 'cyan', 'green', 'yellow']
```

Se pueden utilizar incluso funciones creadas por el desarrollador

```python
def area(x):
	return x[0]*x[1]

p = [(3, 3), (4, 2), (2, 2), (5, 2), (1, 7)]

q = sorted(p, key=area)
print(q) # [(2, 2), (1, 7), (4, 2), (3, 3), (5, 2)]
```

# Funciones lambda

Una función que calcule el área;

```python
lambda x : x[0] * x[1]
```

La palabra reservada `lambda` identifica una expresión lambda. `x` es el parámetro (en este caso solo hay un parámetro). Los puntos `:` finalizan la lista de parámetros e introduce el cuerpo de la función.

```python
q = sorted(p, key = lambda x: x[0]*x[1])
```

El código anterior crea un objeto de tipo función temporal y anónimo; y se pasa a la función `sorted()`. La función sorted() la utiliza para realizar el ordenamiento. Y después desaparece, justo como cualquier otro objeto temporal.

La función son nombre no creada con la función lambda es exactamente igual a la creada con `def`. Si se desea, se puede asignar a una variable:

```python
area = lambda x: x[0]*x[1]
```

Una función lambda puede tener cualquier número de parámetros, incluso ninguno:

```python
lambda: 1  # No arguments
lambda x, y: x + y
lambda a, b, c, d: a * b + c * d
```

Las funciones lambda pueden hacer el código más expresivo o más corto, y por lo tanto más fácil de leer. Algunas sugerencia en su uso son:

- Las funciones lambda solo pueden expresar una sola expresión de Python. Si no puedes expresarlo en una solo línea, no utilizar lambdas.
- Generalmente se utilizan para representar código corto, donde el comportamiento del código es obvio al mirarlo. Si el comportamiento es complicado, es mejor definir una función normal para darle un nombre significativo y agregar comentarios.
- Dado que una expresión lambda se usará como parte de un código más largo, asegurarse que el código en general sigue siendo fácil de leer. Si una llamada a función utiliza muchas expresiones lambda puede resultar difícil de leer lo que se esta haciendo.
- Si la misma función es utilizada en diferentes lugares, es preferible definirla de forma normal, en lugar de repetir la lambda.

A pesar de que las recomendaciones anteriores parecen restrictivas, existen situaciones donde el uso de lambda es perfecto para lo que se necesita.

Dado que una función lambda es un objeto puede ser llamada en lugares como:

```python
a = (lambda x: x + 1)(3)
```

Este ejemplo, no es un uso propio de esta características, porque se podría utilizar

```python
a = 3 + 1
```

# Funciones como retorno de valor

Se pude retornar una función como un valor

```python
def add1():
	return lambda x: x + 1
    
f = add1()
print(f(2))
```

# Versiones de funciones de operadores estándar

El módulo estándar `operator` contiene un conjunto de funciones que son equivalentes a los operadores de Python, por ejemplo:

```python
x = operator.add(a, b) # Equivalent to x = a + b 
x = operator.truediv(a, b) # Equivalent to x = a / b 
x = operator.floordiv(a, b) # Equivalent to x = a // b
```

[operator - Standard operators as functions - Python 3.11.0 documentation](https://docs.python.org/3/library/operator.html)

Son funciones muy prácticas y reemplazan frecuentemente expresiones lambdas. Por ejemplo:

```python
lambda x, y: x + y
```

Es reemplazada por `add()`, una función que toma dos valores y los suma. El uso de funciones estándar es más corto y más declarativo.

Se puede incluso crear una aplicación parcial al drear nuevas funciones basadas en operadores existente. Por ejemplo:

```python
from functools import partial
f = partial(add, 3)
x = f(4) # Equivalent to x = 3 + 7
```

En este caso, `partial` crea una función anónima que toma una variable. Se comporta como add, pero si el primer parámetro ha sido pre-definido a 3. En otras palabras, es equivalente al lambda:

```python
f = lambda x: 3 + x
```

Otros ejemplo de `operator`

```python
operator.lt(a, b)          # a < b
operator.eq(a, b)          # a == b
operator.not(a)            # not a 
operator.neg(a, b)         # -a
operator.getitem(s, i)     # s[i]
operator.setitem(s, i, x)  # s[i] = x
operator.delitem(s, i)     # del s[i]
```

operator también define funciones que retornan funciones. Por ejemplo, `itemgetter()` que retorna un función que funciona de la siguiente forma:

```python
k = [2, 4, 6, 8]
f = operator.itemgetter(2) 
x = f(k) # x = 6
```

En este caso `itemgetter(2)` retorna una función que tomará el número `2` de una lista. Cuando se aplica esta función a una lista `k`, devolverá el segundo elemento, valor `6`. Existen funciones similares para tomar el nombre de un atributo `attrgetter` y llamadas a nombres de métodos `methodcaller`. Estos son ejemplos particulares útiles para el uso del argumento `key` de la función `sorted()`.