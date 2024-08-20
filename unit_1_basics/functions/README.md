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
__Argumentos y parámetros__

En el ejemplo anterior la variable `username` de la definición de la función `greet_user()` es un ejemplo de un __parámetro__, una pieza de información que la función necesita para realizar su trabajo. El valor `'jesse'` es un ejemplo de un __argumento__. Un argumento es una pieza de información que pasa de una _llamada de la función_ a la función.

- [**`Ejemplo 12 - Funciones`**](./ex-functions.ipynb)
- [**`Ejemplo 13 - Funciones con Listas `**]()