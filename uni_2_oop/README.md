# Programación Orientada a objetos en Python

## 1. Objetivos


## Clases y Objetos

La __Programación Orientada a Objetos__ nace de los problemas creados por la programación estructurada y nos ayuda a resolver cierto problemas como:

- Código muy largo: A medida que un sistema va creciendo y se hace más robusta el código generado se vuelve muy extenso haciéndose difícil de leer, depurar, mantener.
- Si algo falla, todo se rompe: Ya que con la programación estructurada el código se ejecuta secuencialmente al momento de que una de esas líneas fallara todo lo demás deja de funcionar.
- Difícil de mantener.

El paradigma de Programación Orientada a Objetos se compone de 4 elementos:

- Clases
- Propiedades
- Métodos
- Objetos

Y se base en 4 Pilares:

- Encapsulamiento
- Abstracción
- Herencia
- Polimorfismo

El uso de UML (Unfied Modeling Language) o Lenguaje de Modelado Unificado es una notación para la creación de diagramas de modelado en Sistemas Oriendatos a Objetos. Lo que permite crear una representación gráfica de los objetos.

[**`Más detalles de UML`**](./uml/README.md)

### Objetos 
En programación orientada a objetos se escriben __clases__ que representa cosas o situaciones de la vida real, y se crean __objetos__ basados en estas clases. 

Cuando se escribe una clase se define el comportamiento que puede tener una categoría de objetos.

El crear un objeto de una clase se le conoce como __instanciación__.

El primer paso es identificar los objetos.

Los Objetos son aquellos que tienen propiedades y comportamientos, también serán **sustantivos**.

- Pueden ser Físicos o Conceptuales

Las **Propiedades** también pueden llamarse atributos y estos también serán **sustantivos**. Algunos atributos o propiedades son nombre, tamaño, forma, estado, etc. **Son todas las características del objeto**.

Los **Comportamientos** serán todas las operaciones que el objeto puede hacer, suelen ser **verbos** o **sustantivos y verbo**. Algunos ejemplos pueden ser que el usuario pueda hacer login y logout.

### La abstracción y las clases

Una **Clase** es el modelo por el cual nuestros objetos se van a construir y nos van a permitir generar más objetos.

Analizamos Objetos para crear **Clases**. Las **Clases** son los modelos sobres los cuales construiremos nuestros objetos.

**Abstracción** es cuando separamos los datos de un objeto para generar un molde.

### Crear de clases

La definición de una clase comienza con la palabra reservada `class`, seguido de un identificador de la clase y termina con `:`. En seguida se especifica el contenido.

Ejemplo: `firs_class.py`

```python
class MyFirstClass:
    pass
```

A continuación ejecutar la terminal `> python -i first_class.py`.

```terminal
>>> a = MyFirstClass()
>>> b = MyFirstClass()
>>> print(a)
>>> print(b)
```

### Agregar atributos

Para asignar valores al atributo en un objeto se utiliza la sintaxis `<objeto>.<atributo> = <valor>` (referido como notación punto).

```python
class Point:
    pass

p1 = Point()
p2 = Point()

p1.x = 5
p1.y = 4

p2.x = 3
p2.y = 6

print(p1.x, p1.y)
print(p2.x, p2.y)
```

### Agregar comportamientos

En Python los métodos tienen el mismo formato que las funciones (nótese el uso de `self` en los parámetros).

Ejemplo:

```python
class Point:
    def reset(self):
        self.x = 0
        self.y = 0

p = Point()
p.reset()
print(p.x, p.y)
```

La diferencia sintactica entre un método y una función es el argumento requerido `self` (PEP8). El argumento `self` es una referencia al objeto que esta invocando el método. El objeto es una instancia de la clase, y algunas veces es nombrada la variable instancia.

Al realizar la llamada a un método no se especifica explícitamente el argumento `self`, Python automáticamente se preocupa por esto.

```terminal
>>> p = Point()
>>> Point.reset(p)
>>> print(p.x, p.y)
```
¿Qué pasa si olvidamos incluir el argumento `self` en la definición de un método?

Paso de multiples argumentos:

```python
import math

class Point:
    def move(self, x: float, y: float) -> None:
        self.x = x
        self.y = y

    def reset(self) -> None:
        self.move(0, 0)

    def calculate_distance(self, other: "Point") -> float:
        return math.hypot(self.x - other.x, self.y - other.y)
```

Ejemplo de uso de la clase:

```terminal
>>> point1 = Point()
>>> point2 = Point()

>>> point1.reset()
>>> point2.move(5, 0)
>>> print(point2.calculate_distance(point1))
>>> assert point2.calculate_distance(point1) ==
point1.calculate_distance(
... point2
... )
>>> point1.move(3, 4)
>>> print(point1.calculate_distance(point2))
4.47213595499958
>>> print(point1.calculate_distance(point1))
0.0
```

### Inicialización de un objeto

Muchos lenguajes de programación utilizan el concepto de _constructor_, es un método especial que inicializa un objeto cuando es creado. Python tiene un constructor y un inicializador. El método constructor `__new__()` es raramente utilizado. El método inicializador `__init__()`

```python
class Point:
    def __init__(self, x: float, y: float) -> None:
        self.move(x, y)

    def move(self, x: float, y: float) -> None:
        self.x = x
        self.y = y

    def reset(self) -> None:
        self.move(0, 0)

    def calculate_distance(self, other: "Point") -> float:
        return math.hypot(self.x - other.x, self.y - other.y)       
```

Ejemplo de uso de constructor:

```python
point = Point(3, 5)
print(point.x, point.y)
```


[**`Ejemplo - Clase Point`**](./code/clases.ipynb)
[**`Ejercicio - Clases: Student & Classroom`**](./code/student-classroom.ipynb)

## Modularidad

La modularidad va muy relacionada con las clases y es un principio de la Programación Orientado a Objetos y va de la mano con el Diseño Modular que significa dividir un sistema en partes pequeñas y estas serán nuestros módulos pudiendo funcionar de manera independiente.

La **modularidad** de nuestro código nos va a permitir

- Reutilizar
- Evitar colapsos
- Hacer nuestro código más mantenible
- Legibilidad
- Resolución rápida de problemas

**Las clases fomentan la modularidad.**

Una buena práctica es separando las clases en archivos diferentes.

[**`Ejemplo - Módulos y paquetes`**](./code/modules-packages.ipynb)

## Control de acceso

En la Programación Orientada a Objetos se tiene un control de acceso (relacionado a la abstracción). La idea es que algunos atributos y comportamientos son marcados como __privados__ o _protected_ (estos solo pueden ser accedidos por la misma clase). Otros son marcados como __protegidos__ o _protected_ que significa que solo esa clase y subclases lo pueden acceder. El resto es __publico__ o _public_ significa que otros objetos tiene permitido acceder.

Python no utiliza estos conceptos, téCnicamente todos los atributos y métodos son accesibles de forma publica. Si algún método no debería ser publico solo se agrega una nota al _docstrings_.

> 🚨 Somos adultos! No hay necesidad de declarar variables privadas cuando se puede ver todo el código.
>
> Por convención se utilizar el carácter `_` (guión bajo) para indicar que es una variable interna y tienes que pensarlo tres veces antes de acceder de manera directa.
>
> Otra forma de recomendar evitar el uso de una variable es con `__` (doble guión bajo) para indicar ofuscación del nombre o _name mangling_. 
>
> Nota: cuando se utiliza ofuscación del nombre o _name mangling_ se antepone el prefijo `_<classname>`.

### Herencia

**Don’t repeat yourself** es una filosofía que promueve la reducción de duplicación en programación, esto nos va a inculcar que no tengamos líneas de código duplicadas.

Toda pieza de información nunca debería ser duplicada debido a que incrementa la dificultad en los cambios y evolución.

La **herencia** nos permite crear nuevas clases a partir de otras, se basa en modelos y conceptos de la vida real. También tenemos una jerarquía de **padre e hijo.**

````python
class Car:
    def __init__(self, id, license, driver, passengers):
        self.id = id
        self.licence = license
        self.driver = driver
        self.pasangers = passengers

class UberX(Car):
    def __init__(self, id, license, driver, passengers, brand, model):
        super().__init__(id, license, driver, passengers)
        self.brand = brand
        self.model = model

class UberBlack(Car):
    def __init__(self, id, license, driver, passingers, typeCarAccepted, seatsMaterial):
        super().__init__(id, license, driver, passengers)
        self.typeCardAccepted = typeCarAccepted
        self.seatsMaterial = seatsMaterial
````

[**`Ejemplo - Herencia`**](./code/inheritance.ipynb)

### Herencia múltiple

En esencia la herencia múltiple permite a una subclase heredar de más de una clase padre sus funcionalidades. 

En el siguiente ejemplo se agrega la funcionalidad _enviar un correo_ a la clase `Contact` a través de un _mixin_.

```python
class Emailable(Protocol):
    email: str

class MailSender(Emailable):
    def send_mail(self, message: str) -> None:
        print(f"Sending mail to {self.email=}")
        # Add e-mail logic here

class EmailableContact(Contact, MailSender):
    pass
```

```python
e = EmailableContact("Jonny B", "j@sloop.net")
Contact.all_contacts

e.send_mail("Hello, test email here")
```

  
## Polimorfismo

El concepto de polimorfismo es un nombre __rimbombante__ para describir un concepto muy simple: diferentes comportamientos ocurren dependiendo de cual sea la subclase que sea utilizada, sin tener que conocer explícitamente qué subclase es.  En algunas ocasiones, se le conoce como el Principio de Liskov Substitution (en honor a Barbara Liskov) que se puede sustituir con cualquier subclase a la superclase.


```python
from pathlib import Path

class AudioFile:
    ext: str

    def __init__(self, filepath: Path) -> None:
        if not filepath.suffix == self.ext:
            raise ValueError("Invalid file format")
    
        self.filepath = filepath

class MP3File(AudioFile):
    ext = ".mp3"
    
    def play(self) -> None:
        print(f"playing {self.filepath} as mp3")

class WavFile(AudioFile):
    ext = ".wav"
    def play(self) -> None:
        print(f"playing {self.filepath} as wav")

class OggFile(AudioFile):
    ext = ".ogg"
    def play(self) -> None:
        print(f"playing {self.filepath} as ogg")
```
