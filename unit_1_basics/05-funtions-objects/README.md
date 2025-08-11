# Funciones como objetos

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

## Funciones lambda

En algunas ocasiones no se requiere nombrar las funciones, particularmente en funciones simples. Por ejemplo:

En la siguiente función se calcula el área:

```python
def area(x):
	return x[0]*x[1]
```

Se puede utilizar procedimientos anónimos mediante el uso de lambda.

```python
lambda x : x[0] * x[1]
```

La palabra reservada `lambda` identifica una expresión lambda. `x` es el parámetro (en este caso solo hay un parámetro). Los puntos `:` finalizan la lista de parámetros e introduce el cuerpo de la función.

```python
q = sorted(p, key = lambda x: x[0]*x[1])
```

El código anterior crea un objeto de tipo función temporal y anónimo; y se pasa a la función `sorted()`. La función sorted() la utiliza para realizar el ordenamiento. Y después desaparece, justo como cualquier otro objeto temporal.

La función lambda es exactamente igual a la creada con `def`. Si se desea, se puede asignar a una variable:

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

- Las funciones lambda __solo pueden expresar una sola expresión__ de Python. Si no puedes expresarlo en una solo línea, no utilizar lambdas.
- Generalmente se utilizan para representar código corto, donde el comportamiento del código es obvio al mirarlo. Si el comportamiento es complicado, es mejor definir una función normal para darle un nombre significativo y agregar comentarios.
- Dado que una expresión lambda se usará como parte de un código más largo, asegurarse que el código en general sigue siendo fácil de leer.
- Si una llamada a función utiliza muchas expresiones lambda puede resultar difícil de leer lo que se esta haciendo.
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

# Cierres o _closures*

En programación funcional, es común escribir funciones que crean otras funciones. Una simple manera y elegante de hacer esto es mediante un cierre. Los cierres proporcionan una manera de crear funciones dinámicamente, como lambdas pero mucho más poderosas. 

## Funciones internas

Una función interna es una función que se define dentro de otra función:

```python
def print3():
	def print_hello():
		print('hello')

	print_hello()
	print_hello()
	print_hello()
    
# Main code
print3()
print_hello()
```

`print_hello()` es una función interna de `print3()`. Especialmente, `print3()` primero define `print_hello()`, después es llamada tres veces.

El resultado cuando se ejecuta el código principal es:

- Llamada de `print3` imprime `“hello”` tres veces.
- Llamado `print_hello` da un error porque solo es visible al interior de `print3`.

**Retorno de una función interna**

Una función puede retornar una función interna

```python
def make_print():
	def print_hello():
		print('hello')
	return print_hello
    
# Main code
fn = make_print()
fn()
```

## Un cierre

Creación de un cierre

```python
def make_printx(x):
	def printx():
		print(x)
	return printx
    
# Main code
fn1 = make_printx(7)
fn2 = make_printx(100)
fn1()
fn2()
```

En esta ocasión la función `make_print` toma un parámetro. Y la función interna `printx`, utiliza ese parámetro. Esto es correcto, dado que una función interna puede accesar las variables locales y los parámetros del cierre de una función.

Cuando se llama `make_printx()` se pasa el valor de `7`. Esto crea un objeto para la función `printx()`, lo interesante de esto es que esa función objeto esta asociada con `x = 7`. La combinación de los objetos de función junto con el valor `x` es llamado cierre.

En el código anterior `fn1()` es un cierre de `printx()` con el valor de `x = 7`, y `fn2()` es un cierre de `printx()` con el valor de `x = 100`. Cuando se llame `fn1()` imprime un `7` y cuando se llame `fn2()` imprime un `100`.

## Uso de cierre

Suponer que se necesita una función que imprima un valor, pero automáticamente el valor debe estar encerrado entre paréntesis. Además se necesita controlar que tipo de paréntesis utilizar como por ejemplo: [x], {x} o <<x>>.

```python
def make_printb(start, end):
        def printb(s):
            print(start + s + end)
        return printb
# Main code
sq = make_printb('[', ']') 
dbl_ang = make_printb('<<', '>>') 
sq('hello')
dbl_ang('world')
```

En este ejemplo, `make_printb()` acepta parámetros para los paréntesis `start` y `end`. Pero en este caso, la función interna `printb()` acepta un parámetro que representa la cadena actual a ser impresa dentro de los paréntesis. Esto significa, que el tipo de paréntesis será ajustado cuando se crea el cierre, pero se puede asignar el contenido cuando se realice la llamada de la función cierre.

Cuando se crea el cierre `sq()` asignamos los corchetes. Cada vez que `sq()` sea llamado, utilizará corchetes, pero el contenido entre los paréntesis puede ser cualquier cosa. de forma similar, `dbl_ang()`, utilizará picoparéntesis dobles.

En este ejemplo, mediante el uso de cierres se ha creado una familia de funciones que imprime  texto entre paréntesis utilizando diferentes estilos.

## Qué es un cierre

Un cierre normalmente requiere tres cosas:

- Una función externa que contenga una función interna
- La función externa tiene parámetros o variables locales.
- La función externa retorna la función interna como un objeto de tipo función.

En términos estrictos, cualquier función que retorna una función interna es un cierre, incluso si no tiene parámetros. Por ejemplo, la función `make_print()`.

## Creación de funciones anónimas

### Una introducción a `map()`

La función `map()` es una función de Python. En su forma más simple acepta una objeto de función y una secuencia (por ejemplo, una lista). Aplica la función a cada elemento de la lista.

```python
a = [2.2, 5.6, 1.9, 0.1]
b = map(round, a)
print(list(b))    # [2, 6, 2, 0]
```

En este caso, se aplica la función `round()` a cada elemento en a. La función `round()` redondea un valor a su entero más cercano. 

### Incrementar los elementos de una lista

Suponer que desea agregar 1 a cada elemento en la lista. Se necesita una función que acepte un único parámetro y sume un 1. Una manera de realizar esto es utilizar lambdas:

```python
lambda x: x + 1
```

Esto crea una función anónima que realiza lo que se necesita. Aplicando `map()` 

```python
a = [1, 3, 0, 6]
b = map(lambda x: x + 1, a)
print(list(b))    # [2, 4, 1, 7]
```

### Utilizar un cierre en lugar de un lambda

Se puede utilizar un cierre para crear una función anónima, en lugar de un lambda:

```python
def addn(n):
	def add(x):
		return x + n
	return add
    
a = [1, 3, 0, 6]
b = map(addn(1), a)
print(list(b))    # [2, 4, 1, 7]
```

La función addn(1) crea una función anónima que suma un 1 a su argumento- exactamente como la función lambda que se definió anteriormente. Esto implica mas código que al utilizar lambda, porque los cierres tienen que ser definidos, pero tienen varias ventajas:

- Si se requiere el uso de la función en más de un lugar, será mejor implementar un cierre.
- El cierre permite crear una familiar de funciones anónimas relacionadas, por ejemplo, add(2) crea una función que agrega 2 a su argumento.
- La función dentro del cierre puede ser tan compleja como sea necesario, mientras que la lambda esta limitada a una sola expresión. Si se requiere de una función compleja es preferible un cierre.

### Otras alternativas

Existen diferentes maneras de crear funciones anónimas, se puede utilizar objetos invocables.

# Composición de funciones

Ejemplo, se require una función que pueda convertir cualquier carácter, por ejemplo `‘a’` en una cadena hex representado su código carácter en ASCII (el cual sería `‘0x61’`.

Existen dos funciones en Python que pueden hacer esto, `ord` convierte un carácter a un valor entero que representa su código ASCII ( o más generalmente su valor Unicode). `hex` convierte un valor `int` a cadena `hex`. Utilizando estás dos funciones se pude definir una función que realice la tarea:

```python
def codestr(c):
	return (hex(ord(c)))

h = codestr('a')
print(h) # '0x61'
```

En este ejemplo se aplica la función `ord()` a `c`, y después se aplica la función `hex()` al resultado. Aplicar una función al resultado de otra función es llamado **composición** de dos funciones.

Definir una función es un procedimiento de hacer cosas. Una forma mucho más funcional puede ser construir una función que haga el trabajo por nosotros:

```python
def compose(f, g):
	def fn(x):
		return f(g(x))
	return fn
    
codestr = compose(hex, ord)
h = codestr('a')
print(h)         # '0x61'
```

Primero, se define una función composición. La composición acepta dos funciones, `f()` y `g()`. Está retorna una función que aplica `g()` a `x` y después aplica `f()` al resultado. Esto es completamente genérico y puede ser usado para realizar la composición de dos funciones. Las únicas condiciones son:

- `f()` y `g()` deben aceptar un único parámetro.
- El valor de retorno de `g()` debe ser un valor válido como parámetro de entrada para `f()`.

El siguiente paso es utilizar `compose()` para crear una función que aplique `ord()` y después `hex()`. Esta función es almacenada en `codestr`, después puede ser llamada con el valor `‘a’` para probar que funciona.

### La ventaja del uso de composiciones

La primera impresión es que el primer código es más simple que el segundo. Pero es necesario recordar que la composición es una función genérica que puede ser utilizada en múltiples ocasiones. Por lo que, el código original luce de la siguiente forma:

```python
def codestr(c):
	return(hex(ord(c)))
```

El código equivalente funcional es:

```python
codestr = compose(hex, ord)
```

El código luce muy similar, pero el código funcional muestra mucho más claramente la intención. La función realiza una composición de la función  `hex()` y la función `ord()`, en el código original, esa intención se expresa como una función que podría estar haciendo cualquier cosa. Hay que leer el código para estar seguro. Puede parecer una diferencia menor, pero con un código más complejo la carga cognitiva puede aumentar.

Un aspecto relacionado es que, siempre que se confíe en `compose`, `hex` y `ord`, entonces la solución funcional tiene que funcionar. ¿cómo podría no funcionar si solo son tres funciones de confianza haciendo lo que tienen que hacer? Con el código original, se tienen dos funciones de confianza más una nueva función que, por lo que se sabe, podría tener un error. De nuevo, no es muy probable, pero estas cosas pueden acumularse en un programa más complejo.

Otra ventaja es que compose, puede utilizarse para crear funciones anónimas. Por ejemplo, se puede utilizar maps para aplicar la función compuesta a una cadena y producir una lista valores hex. Esto nos salva de una fea función lambda.

```python
s='zyx'
b = map(compose(hex, ord), s)
print(list(b)) # ['0x78', '0x79', '0x7a']
```

Si no se esta muy familiarizado con `map()`, funcionará con cadenas tanto como con arreglos, aplicando la función a cada carácter en la cadena y creará un iterador `b` que retornaremos en forma de `list`.

Finalmente podemos utilizar la función compose para crear otras funciones. Por ejemplo, una función que calcula el cuadrado del seno de x

```python
compose(lambda x: x*x, math.sin)
```

## Uso de cierres en lugar de clases

Se desea crear un formateador de números que pueda convertir un número en punto flotante a una cadena, con un número predeterminado de decimales.

```python
class Format():
	def __init__(self, precision):
		self.p = precision
	def format(self, x):
		return '{:.{prec}f}'.format(x, prec=self.p)
```

Esta clase puede utilizarse para crear un objeto para formatear :

```python
format3 = Format(3) 
print(format3.format(1.2345678))
print(Format(5).format(1.2345678))
```

Se pueden utilizar cierres para crear una función de formato de forma similar:

```python
def formatn(precision):
	def format(x):
		return '{:.{prec}f}'.format(x, prec=precision)
	return format
```

```python
format3 = formatn(3)
   
print(format3(1.2345678))
print(formatn(5)(1.2345678))
```

Ambas formas son válidas, no hay nada malo en utilizar una clase, pero un cierre ofrece una forma elegante de solucionar el problema. Generalmente se puede utilizar un cierre en lugar de una clase si:

La clase solo tiene un único método

Los parámetros son definidos en el método `__init__`  y nunca cambian.

Si estas condiciones no se cumple, es preferible utilizar una clase.

## Uso de clases en lugar de cierres

En algunas ocasiones las clases pueden ser llamadas como funciones, lo único que se tiene que hacer es definir al método `__call__` en la clase. Esto es útil saber, pero no es utilizado regularmente.

`__call__` es un de los métodos especiales que ofrece Python para permitir al usuario definir objetos que soporten los operadores de Python. Todos los métodos que tienen dos guiones bajos antes y después del nombre del método, o alternativamente métodos mágicos. El método `__call__` soporta llamadas de funciones.

Ejemplo, modificación de la clase Format, que incluye la método `__call__` en lugar del método previo `format`.

```python
class Format():
	def __init__(self, precision):
		self.p = precision
	def __call__(self, x):
		return '{:.{prec}f}'.format(x, prec=self.p)
```

Ahora se crea un objeto format3 como antes, pero en esta ocasión, con el objetivo de llamarla solo se necesita usar la misma sintaxis que se utiliza al llamar a una función.

```python
format3 = Format(3)
print(format3(1.2345678))
print(Format(5)(1.2345678))
```

Nótese, que format3 no es un objeto función, es un objeto Format. Pero porque soporta `__call__`, se pude utilizar notación de funciones para llamarlo, Y, por supuesto, se puede crear un objeto como `Format(5)` y llamarlo directamente.

Ahora el objeto puede ser utilizado de forma similar que un cierre. Pue bien, ahora el objeto puede utilizarse de manera similar al cierre. ¿Merece la pena hacerlo? Normalmente no, porque definir una clase simple es más engorroso que definir un cierre simple.

Un escenario en la que la clase podría ser una mejor opción es si tiene requisitos de inicialización más complejos. Por ejemplo, supongamos que queremos permitir que el formato especifique el número de decimales y la anchura total de la cadena. Y para permitir más características más adelante, se utilizara un estilo de interfaz fluido. Un formateador de interfaz fluido sería:

```python
class Format():
	def __init__(self):
		self.p = 0
		self.w = 0
	
	def prec(self, n):
		self.p = n
		return self
        
	def width(self, n):
		self.w = n
		return self

	def __call__(self, x):
		return '{:{width}.{prec}f}'.format(x, width=self.w,prec=self.p)
```

La interfaz fluida nos permite inicializar nuestro formateador así:

```python
format3 = Format().width(10).prec(3) 
print(format3(1.2345678))
```

Este tipo de interfaz puede resultar util si el formato tiene muchas opciones, con muchas de ellas opcionales. Puede solamente ser hecho utilizando clases.

 

## Inspección de cierres

Se pude mirar dentro de un cierre para encontrar valores de sus variables. Ejemplo:

```python
def f(x, a, v):
	def g(e):
		print(x, a, v, e)
	return g

c = f(5, 6, 7)
```

Python provee métodos para inspeccionar un objeto más profundamente. En el código anterior la función `f` retorna la función objeto `g`. la cual es asignada a la variable `c`. Dado que el objeto retornado es un cierre, también contiene información acerca de las variables `x`, `a`, `v` y sus valores.

Estas variables son llamadas variables libres (las variables que son pasadas a `f`). En otras palabras, variables que son usadas por `f` pero no definidas dentro de `f`.

Todos los objetos en Python tienen atributos “ocultos” que almacenan información acerca de sus internos. Para los cierres los atributos importantes son: `__code__` and `__closure__`. Estos atributos no están realmente ocultos, por supuesto, se pude obtener una lista de todos ellos utilizando:

```python
dir(c)
```

Esto da una diccionario de los nombres de los elementos:

```python
['__annotations__', '__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__get__', '__getattribute__', '__globals__', '__gt__', '__hash__', '__init__', '__kwdefaults__', '__le__', '__lt__', '__module__', '__name__', '__ne__', '__new__', '__qualname__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
```

Se pueden listar las variables libres de f de la siguiente forma:

```python
print(c.__code__.co_freevars)
```

El resultado es una tupla de valores (`’a’`, `‘v’`, `‘x’`) el cual incluye todas las variables libres. Las variables son ordenan por valores hash, por lo que es seguro tratar con el orden como esencialmente aleatorio.

Se pueden obtener los valores de los atributos `__closures__`. Este contiene un a tupla de celdas, donde cada celda contiene el valor de cada una de las variables. Se accesan de la siguiente forma:

```python
print(c.__closure__[0].cell_contents) 
print(c.__closure__[1].cell_contents) 
print(c.__closure__[2].cell_contents)
```

Esto retorna 6, 7, 5, los valores de `a`, `v` y `x`. Los valores son almacenados en el mismo orden que el nombre de las variables en la tupla `freevars`. Para mostrar la lista de nombres y variables:

```python
for i, name in enumerate(c.__code__.co_freevars): 
	print(name, c.__closure__[i].cell_contents)
```

Esto puede ser util en algunas circunstancias para encontrar detalles de algún cierre en el código. Los valores son de solo lectura y no se pueden modificar.