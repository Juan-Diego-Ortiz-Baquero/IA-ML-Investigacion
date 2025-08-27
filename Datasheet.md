=======
# NumPy – Creación y Manipulación de Arreglos

## Introducción

NumPy es la biblioteca principal para trabajar con arrays en Python. Usar arrays (ndarrays) permite procesar datos de forma eficiente y realizar cálculos matemáticos rápidamente, algo fundamental en ciencia de datos y análisis numérico.

A continuación explico cómo crear arrays, cambiarlos de forma (reshape), concatenarlos y realizar operaciones básicas, con ejemplos probados en Google Colab. En cada sección agrego una breve idea de para qué sirve cada operación.

---

## 1. Creación de arrays

> **¿Para qué sirve?**  
> Los arrays son la base para procesar datos en NumPy. Puedes crearlos a partir de listas, tuplas o usando funciones de la propia librería para generar datos automáticamente.

### Desde listas o tuplas

Convierte listas y tuplas de Python en arrays NumPy. Muy útil para comenzar a trabajar con tus propios datos.

```python
import numpy as np

# Array de una dimensión (1D)
a1 = np.array([1, 2, 3, 4])
print(a1)
# Resultado: [1 2 3 4]

# Array de dos dimensiones (2D)
a2 = np.array([[1, 2], [3, 4]])
print(a2)
# Resultado:
# [[1 2]
#  [3 4]]
```

### Con funciones de NumPy

NumPy ofrece varias funciones para crear arrays rápidamente, ideales para pruebas, inicialización y generación de datos sintéticos.

```python
# arange: secuencia de números
arr = np.arange(0, 6)
print(arr)
# Resultado: [0 1 2 3 4 5]

# zeros y ones
zeros = np.zeros((2, 3))
ones = np.ones((2, 3))
print(zeros)
print(ones)
# Resultado:
# [[0. 0. 0.]
#  [0. 0. 0.]]
# [[1. 1. 1.]
#  [1. 1. 1.]]
```

---

## 2. Cambiar la forma de un array (reshape)

> **¿Para qué sirve?**  
> Muchas veces necesitas reorganizar tus datos para adaptarlos a modelos, gráficos o análisis. Con `reshape` puedes cambiar la estructura del array sin perder la información.

```python
arr = np.arange(6)
reshaped = arr.reshape((2, 3))
print(reshaped)
# Resultado:
# [[0 1 2]
#  [3 4 5]]
```
---

## 3. Concatenar arrays

> **¿Para qué sirve?**  
> Unir arrays te permite agrupar información, combinar resultados o construir estructuras más grandes a partir de datos pequeños.

Unir arrays puede hacerse horizontal o verticalmente.

```python
a = np.array([[1, 2], [3, 4]])
b = np.array([[5, 6]])

# Vertical (añadir filas)
v_concat = np.vstack((a, b))
print(v_concat)
# Resultado:
# [[1 2]
#  [3 4]
#  [5 6]]

# Horizontal (añadir columnas)
c = np.array([[7], [8], [9]])
h_concat = np.hstack((v_concat, c))
print(h_concat)
# Resultado:
# [[1 2 7]
#  [3 4 8]
#  [5 6 9]]
```
Para arrays 1D, se puede usar `concatenate`:

```python
x = np.array([1, 2, 3])
y = np.array([4, 5, 6])
xy = np.concatenate([x, y])
print(xy)
# Resultado: [1 2 3 4 5 6]
```
---

## 4. Operaciones básicas con arrays

> **¿Para qué sirve?**  
> Las operaciones matemáticas sobre arrays son esenciales para análisis, procesamiento de señales, estadística y cualquier cálculo sobre datos. NumPy permite operar sobre todos los elementos sin necesidad de escribir bucles.

Las operaciones matemáticas se aplican a todos los elementos. No es necesario recorrer el array con for.

```python
arr = np.array([2, 4, 6, 8])

# Suma y resta
print(arr + 1)      # [3 5 7 9]
print(arr - 1)      # [1 3 5 7]

# Multiplicación y división
print(arr * 2)      # [ 4  8 12 16]
print(arr / 2)      # [1. 2. 3. 4.]

# Potencias y raíz
print(arr ** 2)     # [ 4 16 36 64]
print(np.sqrt(arr)) # [1.41421356 2.         2.44948974 2.82842712]
```

Operaciones entre arrays:

```python
a = np.array([1, 2, 3])
b = np.array([10, 20, 30])
print(a + b)        # [11 22 33]
print(a * b)        # [10 40 90]
```
---
# NumPy – Operaciones estadísticas y funciones avanzadas

## Introducción

NumPy no solo sirve para crear arrays y hacer operaciones básicas, también incluye muchas funciones estadísticas, de generación de datos y de álgebra lineal. Estas funciones son esenciales para análisis de datos y cálculos científicos, ya que permiten obtener información resumida, generar datos sintéticos y resolver problemas matemáticos complejos de forma eficiente.

## 1. Operaciones estadísticas básicas

### Promedio (`mean`), desviación estándar (`std`), suma (`sum`)

Estas funciones permiten obtener estadísticas rápidas sobre los datos contenidos en un array.

```python
import numpy as np

arr = np.array([1, 2, 3, 4, 5])

print(np.mean(arr))  # Promedio: 3.0
print(np.std(arr))   # Desviación estándar: 1.41421...
print(np.sum(arr))   # Suma: 15
```

Para arrays multidimensionales, se puede especificar el eje (`axis`) sobre el cual calcular:

```python
mat = np.array([[1, 2], [3, 4]])

print(np.mean(mat, axis=0))  # Promedio por columna: [2. 3.]
print(np.mean(mat, axis=1))  # Promedio por fila: [1.5 3.5]
```
---

## 2. Generación de datos: `arange`, `linspace`, `random`

### `arange` y `linspace`

Estas funciones crean arrays numéricos con distintos criterios:

```python
# arange: números enteros (o decimales) en un rango
a = np.arange(0, 10, 2)
print(a)  # [0 2 4 6 8]

# linspace: números equiespaciados entre dos valores
b = np.linspace(0, 1, 5)
print(b)  # [0.   0.25 0.5  0.75 1.  ]
```

### Datos aleatorios con `random`

NumPy incluye funciones para generar números aleatorios, útiles para simulaciones y pruebas.

```python
rng = np.random.default_rng(42)

# Array aleatorio de 3 números entre 0 y 1
rand_arr = rng.random(3)
print(rand_arr)  # [0.77395605 0.43887844 0.85859792]

# Array aleatorio entero entre 0 y 9, forma (2, 2)
rand_int = rng.integers(0, 10, size=(2, 2))
print(rand_int)
# Resultado:
# [[8 0]
#  [2 6]]
```

---

## 3. Álgebra lineal

NumPy tiene funciones avanzadas para trabajar con matrices y resolver problemas de álgebra lineal.

### Producto de matrices

```python
A = np.array([[1, 2], [3, 4]])
B = np.array([[2, 0], [1, 2]])

# Producto matricial
prod = np.dot(A, B)
print(prod)
# Resultado:
# [[4  4]
#  [10 8]]
```

Desde Python 3.5 también se puede usar el operador `@` para multiplicación de matrices:

```python
print(A @ B)
# Mismo resultado que np.dot
```

### Transpuesta y determinante

```python
print(A.T)            # Transpuesta
print(np.linalg.det(A)) # Determinante: -2.0
```

### Inversa de una matriz

```python
invA = np.linalg.inv(A)
print(invA)
# Resultado:
# [[-2.   1. ]
#  [ 1.5 -0.5]]
```

### Solución de sistemas lineales

```python
# Ax = b
b = np.array([5, 6])
x = np.linalg.solve(A, b)
print(x)
# Resultado: [ -4.  4.5 ]
```
## Fuentes


- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1N8QNpHXhRpXT9cR7vjnGT1Z9xvYeEERU?usp=sharing
- Linear algebra — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.linalg.html
- Random sampling — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/random/index.html
- Statistics — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.statistics.html
- Array creation — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/user/basics.creation.html
- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1y9wOg9nnFlTXrY3lGtamlAhoPrmmGye0?authuser=1 [Ejecuciones propias en Google Colab] 
- Sherrill, D. [@CodeWithDerrick]. (s/f). Introduction to NumPy arrays for beginners - learn NumPy series [[Object Object]]. Youtube. Recuperado el 26 de agosto de 2025, de https://www.youtube.com/watch?v=9fcTq8PDWWA

