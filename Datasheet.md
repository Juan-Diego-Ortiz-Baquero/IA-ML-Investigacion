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

---

## Fuentes


- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1N8QNpHXhRpXT9cR7vjnGT1Z9xvYeEERU?usp=sharing
- Linear algebra — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.linalg.html
- Random sampling — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/random/index.html
- Statistics — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.statistics.html