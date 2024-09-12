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

````python
class Student():
    def __init__(self, first_name, last_name, major):
        self.first_name = first_name
        self.last_name = last_name
        self.major = major

    def
````

[**`Ejemplo - Clases`**](./code/clases.ipynb)
[**`Ejercicio - Clases: Student & Classroom`**](./code/student-classroom.ipynb)

### Modularidad

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

## Herencia

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

## Polimorfismo

El concepto de polimorfismo es un nombre __rimbombante__ de describir un concepto muy simple: diferentes comportamientos ocurren dependiendo de cual sea la subclase que sea utilizada, sin tener que conocer explicitamente qué subclase es.  En algunas ocasiones, se le conoce como el Principio de Liskov Substitution en honor a Barbara Liskov, la cual dice, que se puede sustituir con cualquier subclase a la superclase.


