## Ejercicios

Para la siguiente sección de ejecicios se recomienda evitar en lo posible el uso de funciones definidas en modulos o bibliotecas de python.

### 6.1. Función para determinar la positividad de un número
Escribe una función llamada `determinar_positividad(n)` que reciba un número entero `n` como argumento. La función debe devolver la letra `'P'` si el número es positivo, y la letra `'N'` si es cero o negativo.

### 6.2. Función para verificar divisibilidad
Escribe una función llamada `es_divisible(a, b)` que reciba dos números enteros `a` y `b`. La función debe devolver `True` si `a` es divisible por `b` o viceversa, y `False` en caso contrario.

### 6.3. Conversión de Celsius a Fahrenheit
Crea una función llamada `celsius_a_fahrenheit(c)` que convierta una temperatura dada en grados Celsius a grados Fahrenheit. La fórmula de conversión es: 
$ F = \frac{9}{5} C + 32 $

### 6.4. Verificación de dígito
Escribe una función llamada `es_digito(caracter)` que determine si un carácter dado es uno de los dígitos del 0 al 9. La función debe devolver `True` si es un dígito, y `False` en caso contrario.

### 6.5. Verificación de vocal
Crea una función llamada `es_vocal(caracter)` que determine si un carácter dado es una vocal (a, e, i, o, u). La función debe devolver `True` si es una vocal, y `False` en caso contrario.

### 6.6. Redondeo de números
Escribe una función llamada `redondear(cantidad, decimales)` que acepte un valor real `cantidad` y un valor entero `decimales`. La función debe devolver `cantidad` redondeada al número especificado de decimales. Por ejemplo, `redondear(20.562, 2)` debe devolver `20.56`.

### 6.7. Mayor de dos números
Crea una función llamada `maximo(a, b)` que reciba dos números y devuelva el mayor de ellos.

### 6.8. Generación de números primos
Escribe una función llamada `generar_primos(n)` que calcule y devuelva una lista con los primeros `n` números primos.

---

## Problemas

### 6.1. Inversión de una cadena
Escribe una función llamada `invertir_cadena(cadena)` que reciba una cadena de caracteres y la devuelva en forma inversa. Por ejemplo, la cadena `"hola"` debe convertirse en `"aloh"`.

### 6.2. Verificación de palíndromo
Crea una función llamada `es_palindromo(cadena)` que determine si una cadena de caracteres es un palíndromo. Un palíndromo es un texto que se lee igual en sentido directo e inverso, como `"radar"`.

### 6.3. Formato de fecha
Escribe una función llamada `formato_fecha(dia, mes, anio)` que reciba un número de día, mes y año y lo visualice en formato `dd/mm/aa`. Por ejemplo, los valores `8, 10, 1946` deben visualizarse como `8/10/46`.

### 6.4. Conversión de coordenadas polares a rectangulares
Crea una función llamada `polares_a_rectangulares(r, theta)` que convierta coordenadas polares `(r, θ)` a coordenadas rectangulares `(x, y)`. 

### 6.5. Factores primos de un número
Escribe un programa que lea un número entero positivo y luego llame a una función `factores_primos(n)` que visualice los factores primos de ese número.

### 6.6. Visualización de un calendario
Crea un programa que, mediante la implemetación de una función, visualice un calendario de un mes y un año especificado. El usuario debe ingresar el mes y el año, y la función debe imprimir el calendario correspondiente.

Por ejemplo, si se ingresa como mes febrero(2) y año 2021, la impresión en pantalla será:

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

Para conocer los días correctos de la semana para cada día del mes, investiga sobre el calendario perpetuo. 


### 6.7. Cambio de base
Escribe un programa que lea dos enteros positivos `n` y `b`, luego llame a una función `cambiar_base(n, b)` para calcular y visualizar la representación del número `n` que se encuentra en base decimal, y será convertido a base `b`. Para realizar el cambio puedes usar un algoritmo basado en divisiones sucesivas.

Por ejemplo, el resultado de la llamada a la función: `cambiar_base(34, 8)` será igual a  42.

### 6.8. Cálculo del máximo común divisor
Crea un programa que permita calcular el máximo común divisor (`mcd`) de dos números usando el algoritmo de Euclides. La función `mcd(a, b)` debe devolver el `mcd` de `a` y `b`.

### 6.9. Inverso de un número
Escribe una función llamada `inverso_numero(n)` que devuelva el inverso de un número dado. Por ejemplo, el inverso de `1234` es `4321`.

### 6.10. Cálculo del coeficiente binomial
Crea una función llamada `coeficiente_binomial(m, n)` que calcule el coeficiente binomial usando la fórmula:
$ \binom{m}{n} = \frac{m!}{n!(m-n)!} $

### 6.11. Suma de una progresión geométrica
Escribe un programa que lea dos números `x` y `n` y luego use una función `suma_progresion(x, n)` para calcular la suma de la progresión geométrica:
$ 1 + x + x^2 + x^3 + \cdots + x^n $

### 6.12. Análisis de datos de entrada
Crea un programa que permita introducir una serie de números y luego utilice funciones para encontrar el valor mayor, el valor menor, y la suma de los datos. También debe calcular la media de los datos.

### 6.13. Cálculo de una función matemática
Escribe una función llamada `calcular_valor(x)` que acepte un parámetro `x` (donde `x \neq 0`) y devuelva el siguiente valor:
$ x^5(e^{2x}-1) $

### 6.14. Cálculo de una expresión matemática
Crea una función llamada `calcular_expresion(x, n)` que acepte dos parámetros `x` y `n`. La función debe devolver:
- Si $x \geq 0$: $ x + \frac{x^n}{n} - \frac{x^{n+2}}{n+2} $
- Si $x < 0$: $ \frac{x^{n+1}}{n + 1} - \frac{x^{n-1}}{n-1} $

### 6.15. Cálculo del área de un triángulo
Escribe una función llamada `area_triangulo(a, b, c)` que reciba las longitudes de los tres lados de un triángulo (`a`, `b`, `c`) y devuelva el área del triángulo usando la fórmula de Herón:
$ Área = \sqrt{p(p-a)(p-b)(p-c)} $
donde $ p = \frac{a+b+c}{2} $

### 6.16. Funciones de calendario
Escribe un programa mediante funciones que realice las siguientes tareas:
  1. Devuelva el nombre del día de la semana en respuesta a la entrada de la letra inicial (mayúscula o minúscula) de dicho día.
  2. Determine el número de días de un mes dado.

### 6.17. Conversión de números romanos a arábigos
Crea un programa que lea una cadena de hasta diez caracteres que representan un número en numeración romana y visualice el número romano y su equivalente en numeración arábiga. La función debe comprobar con los siguientes datos: `LXXXVI (86)`, `CCCXIX (319)`, `MCCLIV (1254)`.

### 6.18. Puntos dentro de un triángulo
Escribe una función llamada `puntos_dentro_triangulo(v1, v2, v3)` que calcule cuántos puntos de coordenadas enteras existen dentro de un triángulo, dado por las coordenadas de sus tres vértices `(v1, v2, v3)`.

### 6.19. Área de la circunferencia circunscrita
Crea un programa que, mediante funciones, determine el área de la circunferencia circunscrita de un triángulo, dado por las coordenadas de sus tres vértices.

### 6.20. Cálculo de funciones trigonométricas
Dado el valor de un ángulo $θ$, escribe una función llamada `funciones_trigonometricas(theta)` que muestre el valor de todas las funciones trigonométricas correspondientes a ese ángulo (`sin`, `cos`, `tan`, `sec`, `csc`, `cot`).

---