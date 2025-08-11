# Ejercicios y Reglas de Entrega

## Instrucciones Generales

1. **Organización en módulos**
   - Cada función debe definirse en un archivo independiente (o agrupadas por tema en un módulo) y ser utilizada desde otro script diferente (por ejemplo, `main.py`).
   - Estructura sugerida:
  
     ```
     ejercicios/
       ├─ mod_/              # carpeta opcional por tema (p.ej. “numeros”, “cadenas”)
       │   └─ utilidades.py  # aquí defines funciones
       ├─ main.py            # aquí importas y usas las funciones
       └─ README.md          # opcional: cómo ejecutar
     ```

   - No se aceptarán soluciones implementadas y ejecutadas en el mismo archivo sin demostrar la importación desde otro script.

2. **Importaciones**
   - Usa importaciones explícitas: `from utilidades import mi_funcion`.
   - Evita `import *`.

3. **Type hints**
   - Obligatorio anotar tipos en parámetros y valores de retorno de todas las funciones.
   - Ejemplo: `def suma(a: int, b: int) -> int:`

4. **Docstrings**
   - Todas las funciones deben incluir un docstring con:
     - Descripción
     - Parámetros y tipos
     - Valor de retorno y tipo
     - Precondiciones o casos especiales

5. **Estilo PEP‑8**
   - Nombres en `snake_case`, 4 espacios de indentación, líneas ≤ 79–99 caracteres.
   - Recomendado: verificar con `flake8` o formatear con `black`.

6. **Ejecución y evidencias para el reporte en PDF**
   - Ejecutar siempre desde el script “cliente” (`main.py`).
   - Incluir evidencia de ejecución (captura o texto con salidas representativas).
   - Verificación de tipos con `mypy`.

---

## Ejercicios 

### 1. Inversión de una cadena
Escribe una función llamada `invertir_cadena(cadena)` que reciba una cadena de caracteres y la devuelva en forma inversa. Por ejemplo, la cadena `"hola"` debe convertirse en `"aloh"`.

### 2. Verificación de palíndromo
Crea una función llamada `es_palindromo(cadena)` que determine si una cadena de caracteres es un palíndromo. Un palíndromo es un texto que se lee igual en sentido directo e inverso, como `"radar"`.

### 3. Formato de fecha
Escribe una función llamada `formato_fecha(dia, mes, anio)` que reciba un número de día, mes y año, y lo visualice en formato `dd/mm/aa`. Por ejemplo, los valores `8, 10, 1946` deben visualizarse como `8/10/46`.

### 4. Conversión de coordenadas polares a rectangulares
Crea una función llamada `polares_a_rectangulares(r, theta)` que convierta coordenadas polares `(r, θ)` a coordenadas rectangulares `(x, y)`.

### 5. Factores primos de un número
Escribe un programa que lea un número entero positivo y luego llame a una función `factores_primos(n)` que visualice los factores primos de ese número.

_¿Cómo se encuentran los factores primos?_

Para encontrar los factores primos de un número, se divide repetidamente por los números primos más pequeños (2, 3, 5, 7, etc.) hasta que el resultado sea 1. Aquí tienes un proceso paso a paso:

1. Divide el número por el menor número primo posible (que es 2) y sigue dividiendo hasta que ya no sea divisible.  
2. Pasa al siguiente número primo (3, luego 5, etc.) y repite el proceso.  
3. Continúa hasta que el número restante sea 1.

Ejemplo práctico:

Supongamos que queremos encontrar los factores primos de 60.

1. Dividimos 60 por 2 (el menor número primo):  
60 ÷ 2 = 30

2. Dividimos 30 por 2 de nuevo:  
30 ÷ 2 = 15

3. El 15 ya no es divisible por 2, así que pasamos al siguiente número primo, que es 3:  
15 ÷ 3 = 5

4. El 5 es un número primo, así que lo dejamos como está.

Los factores primos de 60 son 2, 2, 3 y 5, o bien:  
$60 = 2^2 \times 3 \times 5$

### 6. Visualización de un calendario
Crea un programa que, mediante la implementación de una función, visualice un calendario de un mes y un año especificados. El usuario debe ingresar el mes y el año, y la función debe imprimir el calendario correspondiente.

Por ejemplo, si se ingresa como mes febrero (2) y año 2021, la impresión en pantalla será:

````text
2021
Febrero
L   M   Mi  J   V   S   D
    1   2   3   4   5   6
7   8   9   10  11  12  13
14  15  16  17  18  19  20
21  22  23  24  25  26  27
28
````

---

## Ejemplo genérico de entrega

**Archivo:** `utilidades.py`
```python
"""
 utilidades.py
 Funciones de ejemplo para ejercicios del curso.
"""

from typing import Sequence

def cuenta_mayores(valores: Sequence[int], umbral: int) -> int:
    """
    Cuenta cuántos elementos de `valores` son estrictamente mayores que `umbral`.

    Parámetros
    ----------
    valores : Sequence[int]
        Secuencia de enteros a evaluar.
    umbral : int
        Valor umbral de comparación.

    Retorna
    -------
    int
        Número de elementos > umbral.

    Precondiciones
    --------------
    - `valores` puede ser lista o tupla de int.
    """
    contador: int = 0
    for v in valores:
        if v > umbral:
            contador += 1
    return contador
```

**Archivo:** `main.py`
```python
from utilidades import cuenta_mayores

def main() -> None:
    datos = [1, 5, 7, 2, 10]
    k = 5
    resultado = cuenta_mayores(datos, k)
    print(f"Hay {resultado} valores mayores que {k} en {datos}")

if __name__ == "__main__":
    main()
```

**Ejecución:**
```bash
python main.py
```

**Verificación de tipos (opcional):**
```bash
mypy utilidades.py main.py
```
