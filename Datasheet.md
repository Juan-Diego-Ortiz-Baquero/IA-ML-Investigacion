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
<img width="812" height="256" alt="image" src="https://github.com/user-attachments/assets/2c1ff9ac-a268-4cab-bb30-93579564f550" />


# Array de dos dimensiones (2D)
a2 = np.array([[1, 2], [3, 4]])
print(a2)
# Resultado:
# [[1 2]
#  [3 4]]
<img width="317" height="152" alt="image" src="https://github.com/user-attachments/assets/99a5ee00-5e19-442d-899d-9a99b20ef52c" />

```

### Con funciones de NumPy

NumPy ofrece varias funciones para crear arrays rápidamente, ideales para pruebas, inicialización y generación de datos sintéticos.

```python
# arange: secuencia de números
arr = np.arange(0, 6)
print(arr)
# Resultado: [0 1 2 3 4 5]
<img width="970" height="235" alt="image" src="https://github.com/user-attachments/assets/255fa421-b705-4291-b295-12c1930dc966" />


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
<img width="279" height="204" alt="image" src="https://github.com/user-attachments/assets/c3dc5a73-4814-4192-a7b1-4c565c0b7499" />

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
<img width="352" height="179" alt="image" src="https://github.com/user-attachments/assets/7ac09b51-d67a-426e-8cd2-ff94beca8d4e" />

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
<img width="407" height="307" alt="image" src="https://github.com/user-attachments/assets/71bb0724-65c7-416d-8991-b052a740c4db" />


# Horizontal (añadir columnas)
c = np.array([[7], [8], [9]])
h_concat = np.hstack((v_concat, c))
print(h_concat)
# Resultado:
# [[1 2 7]
#  [3 4 8]
#  [5 6 9]]
<img width="329" height="169" alt="image" src="https://github.com/user-attachments/assets/c41ea887-1dd4-43c5-8a87-21dea7480c22" />

```

Para arrays 1D, se puede usar `concatenate`:

```python
x = np.array([1, 2, 3])
y = np.array([4, 5, 6])
xy = np.concatenate([x, y])
print(xy)
# Resultado: [1 2 3 4 5 6]
<img width="274" height="132" alt="image" src="https://github.com/user-attachments/assets/d07bcd90-05b9-46e2-9b81-ab17c9bda19f" />

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
<img width="434" height="457" alt="image" src="https://github.com/user-attachments/assets/0bb7d45d-bb92-4f6d-ac79-c8a904ae53d3" />

```

Operaciones entre arrays:

```python
a = np.array([1, 2, 3])
b = np.array([10, 20, 30])
print(a + b)        # [11 22 33]
print(a * b)        # [10 40 90]
<img width="272" height="195" alt="image" src="https://github.com/user-attachments/assets/49bce93b-616d-43a3-a8eb-57292b441ce3" />

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
<img width="701" height="372" alt="image" src="https://github.com/user-attachments/assets/d2b5cd9d-aeae-4cc0-83a7-2d690ad146e0" />

```

Para arrays multidimensionales, se puede especificar el eje (`axis`) sobre el cual calcular:

```python
mat = np.array([[1, 2], [3, 4]])

print(np.mean(mat, axis=0))  # Promedio por columna: [2. 3.]
print(np.mean(mat, axis=1))  # Promedio por fila: [1.5 3.5]
<img width="648" height="198" alt="image" src="https://github.com/user-attachments/assets/2b2f82c4-3409-4f7e-bd8a-a6f30fc13946" />

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
<img width="601" height="350" alt="image" src="https://github.com/user-attachments/assets/eac48384-50fc-4c61-ae4e-24031c9caa6f" />

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
# [[0 6]
#  [2 0]]
<img width="700" height="366" alt="image" src="https://github.com/user-attachments/assets/26b492b3-b9ed-44a5-ae2c-53ef7c65ef54" />


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
<img width="743" height="326" alt="image" src="https://github.com/user-attachments/assets/b24fc293-76d3-4010-8d1a-670c391ca848" />

```

Desde Python 3.5 también se puede usar el operador `@` para multiplicación de matrices:

```python
print(A @ B)
# Mismo resultado que np.dot
<img width="651" height="173" alt="image" src="https://github.com/user-attachments/assets/7e88fc1d-b411-45a2-a245-6e69e962ff90" />

```

### Transpuesta y determinante

```python
print(A.T)            # Transpuesta
print(np.linalg.det(A)) # Determinante: -2.0
<img width="307" height="180" alt="image" src="https://github.com/user-attachments/assets/05cc21b4-7a9d-475c-bed9-6e6a3f73ebab" />

```

### Inversa de una matriz

```python
invA = np.linalg.inv(A)
print(invA)
# Resultado:
# [[-2.   1. ]
#  [ 1.5 -0.5]]
<img width="249" height="153" alt="image" src="https://github.com/user-attachments/assets/0de095b1-b45b-4862-b502-242b26b5ce99" />

```

### Solución de sistemas lineales

```python
# Ax = b
b = np.array([5, 6])
x = np.linalg.solve(A, b)
print(x)
# Resultado: [ -4.  4.5 ]
<img width="331" height="185" alt="image" src="https://github.com/user-attachments/assets/6da547ae-78cc-42b8-a0fb-c9b059247bf2" />

```


---

# Pandas - Creación y manipulación de DataFrames y Series

## Introducción

Pandas es la biblioteca más utilizada para manejo y análisis de datos en Python. Sus dos estructuras principales son `DataFrames` (tabla de datos) y `Series` archivos, seleccionar columnas y filas, y trabajar fácilmente con diferentes tipos de datos.

---

## 1. Crear DataFrames y Series

> **¿Para qué sirve?**
> Los DataFrames son como hojas de cálculo o tablas, y las Series son como una columna individual con etiquetas.

## Crear un DataFrame desde un diccionario o lista

```python
import pandas as pd

# Desde diccionario
df = pd.DataFrame({'A': [1, 2, 3], 'B': ['a', 'b', 'c']})
print(df)
# Resultado:
#    A  B
# 0  1  a
# 1  2  b
# 2  3  c
<img width="532" height="326" alt="image" src="https://github.com/user-attachments/assets/8a2e7eea-18c4-49b7-9016-9f45debd2204" />


# Desde lista de listas
df2 = pd.DataFrame([[10, 20], [30, 40]], columns=['X', 'Y'])
print(df2)
# Resultado:
#     X   Y
# 0  10  20
# 1  30  40
<img width="535" height="154" alt="image" src="https://github.com/user-attachments/assets/a832bd59-45ef-48ea-be49-1ce87f5876d2" />

```

### Crear una Series
```python
s = pd.Series([4, 7, 9], index =['a', 'b', 'c'])
print(s)
# Resultado:
# a   4
# b   7 
# c   9
# dtype: int64
<img width="438" height="195" alt="image" src="https://github.com/user-attachments/assets/be5b6649-e821-435c-8d92-08799fc6e423" />

```

---

## 2. Cargar datos desde archivo

> **¿Para qué sirve?**
> Pandas puede leer datos directamente de archivos CSV, Excel, SQL, etc.

```python
# Leer CSV
df = pd.read_csv('archivo.csv')
print(df.head()) #Ver las primeras filas

# Leer Excel
df_excel = pd.read_excel('archivo.xlsx')
print(df_excel.head())
<img width="442" height="262" alt="image" src="https://github.com/user-attachments/assets/feced9a6-b5e1-41f1-a8bd-d0f1046b3cfc" />

```

---

## 3. Selección de columnas y filas

> **¿Para qué sirve?**
> Permite acceder y manipular partes específicas del DataFrame para análisis o transformación

## Seleccionar columnas

```python
# Una Columna
print(df['A'])
<img width="392" height="259" alt="image" src="https://github.com/user-attachments/assets/5bdbd0f3-4910-4378-8de0-5d0d2b278a62" />


# Varias Columnas
print(df[['A', 'B']])
<img width="215" height="149" alt="image" src="https://github.com/user-attachments/assets/0c76b8ef-e77b-4fa3-90f2-27b685adae96" />

```

### Seleccionar filas (por índice, posición o condición)

```python
# Primera fila por posición
print(df.iloc[0])
# Resultado
# A    1
# B    a
# Name: 0, dtype: object
<img width="498" height="177" alt="image" src="https://github.com/user-attachments/assets/53a8f803-3b19-46b6-b29b-dcd2ec66b5b6" />


# Fila por etiqueta (Si hay índices personalizados)
print(df.iloc[0])
# Resultado
# A    1
# B    a
# Name: 0, dtype: object
<img width="461" height="134" alt="image" src="https://github.com/user-attachments/assets/7e703ede-0265-48aa-bbb2-8b7a336c2c26" />


# Filas por condición
print(df[df['A'] > 1])
# Resultado
#    A  B
# 1  2  b
# 2  3  c
<img width="258" height="141" alt="image" src="https://github.com/user-attachments/assets/006460b8-cac9-471e-85b9-e1353d144823" />

```

---

## 4. Tipos de datos y conversión

> **¿Para qué sirve?**
> Es importante conocer y convertir los tipos de datos para evitar errores y para aplicar funciones correctamente.

```python
print(df.dtypes) # Ver tipo de cada columna
# Resultado
# A     int64
# B    object
# dtype: object
<img width="397" height="169" alt="image" src="https://github.com/user-attachments/assets/a4196cd8-c2b7-4726-bc4b-2404c48aaf09" />


# Covertir tipo de columna
df['A'] = df['A'].astype(float)
print(df.dtypes)
# Resultado
# A    float64
# B     object
# dtype: object
<img width="310" height="149" alt="image" src="https://github.com/user-attachments/assets/81d5f8a6-2f73-4c8d-b2dd-acd84dc604ba" />

```
---

# Pandas - Operaciones avanzada en DataFrames

## Introducción

Además de las funciones básicas, Pandas permite realizar operaciones avanzadas sobre DataFrames para analizar y transformar datos de manera eficiente. Se muenstran ejemplos comunes y útiles para filtrar datos, agrupar y resumir información, combinar tablas, manejar valores nulos y expoortar o importar datos.

## 1. Filtros

> **¿Para qué sirve?**
> Seleccionar filas según condiciones, por ejemplo, extraer datos relevantes de una tabla grande.

```python
import pandas as pd

df = pd.DataFrame({
    'A': [1, 2, 3, 4, 5,],
    'B': ['x', 'y', 'x', 'y', 'x']
})

# Filas donde A es mayor que 2
print(df[df['A'] > 2])
# Resultado
#    A  B
# 2  3  x
# 3  4  y
# 4  5  x

# Filas donde B es 'x'
print(df[df['B'] == 'x'])
# Resultado
#    A  B
# 0  1  x
# 2  3  x
# 4  5  x
<img width="334" height="453" alt="image" src="https://github.com/user-attachments/assets/fdc775e4-deda-4536-adbe-010a2d51a528" />

```

---

## 2. Agrupación y resumen (`groupby`)

> **¿Para qué sirve?**
> Agrupar datos por categorías y calcular sumas, promedios u otras estadísticas dentro de cada grupo.

```python
# Agrupar por columna B y calcular promedio de A
grouped = df.groupby('B')['A'].mean()
print(grouped)
# Resultado:
# B
# x    3.0
# y    3.0
# Name: A, dtype: float64
<img width="420" height="221" alt="image" src="https://github.com/user-attachments/assets/f6626d8a-9fc2-42b6-a8a8-8227663f7aec" />

```
Tambíen se pueden usar otras funciones como `sum()`, `count`, `max`, etc.

---

## 3. Unir DataFrames (`merge` / `join`)

> **¿Para qué sirve?**
> Combinar información de dos tablas según una columna común (como clave).

```python
df1 = pd.DataFrame({'key': ['a', 'b', 'c'], 'value1': [1, 2, 3]})
df2 = pd.DataFrame({'key': ['a', 'b', 'c'], 'value2': [4, 5, 6]})

# Merge por columna 'key'
merged = pd.merge(df1, df2, on='key', how='outer')
print(merged)
# Resultado
#   key  value1  value2
# 0   a     1.0     4.0
# 1   b     2.0     5.0
# 2   c     3.0     NaN
# 3   d     NaN     6.0
<img width="562" height="278" alt="image" src="https://github.com/user-attachments/assets/f2e0e3e1-04bf-40dd-9844-71f4f7a83b04" />

```

---

## 4. Manejo de valores nulos

> **¿Para qué sirve?**
> Identificar, eliminar o reemplazar datos faltantes para evitar errores en el análisis.

```python
# Detectar valores nulos
print(df.isnull())

# Eliminar filas con valores nulos
print(df.dropna())

# Reemplazar nulos con un valor específico
print(df.fillna(0))
```

---

## 5. Exportación e importación de datos

> **¿Para qué sirve?**
> Guardar resultados en archivos o cargar datos externos para análisis.

```python
# Exportar a CSV
df.to_csv('mi_dataframe.csv', index=False)

# Importar desde CSV
nuevo_df = pd.read_csv('mi_dataframe.csv')
print(nuevo_df)
```

Pandas también soporta otros formatos como Excel (`.xlsx`), JSON, HTML, SQL, entre otros.

---

## Fuentes

- Array creation — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/user/basics.creation.html
- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1y9wOg9nnFlTXrY3lGtamlAhoPrmmGye0?authuser=1 [Ejecuciones propias en Google Colab] 
- Sherrill, D. [@CodeWithDerrick]. (s/f). Introduction to NumPy arrays for beginners - learn NumPy series [[Object Object]]. Youtube. Recuperado el 26 de agosto de 2025, de https://www.youtube.com/watch?v=9fcTq8PDWWA
- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1N8QNpHXhRpXT9cR7vjnGT1Z9xvYeEERU?usp=sharing
- Linear algebra — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.linalg.html
- Random sampling — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/random/index.html
- Statistics — NumPy v2.3 manual. (s/f). Numpy.org. Recuperado el 26 de agosto de 2025, de https://numpy.org/doc/stable/reference/routines.statistics.html
- Pandas documentation — pandas 2.3.2 documentation. (s/f). Pydata.org. Recuperado el 26 de agosto de 2025, de https://pandas.pydata.org/docs
- Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/139UHZ81kjxan6cPhKPKgZy_Rh65u0_ry?usp=sharing [Ejercicios]
- [Ejecuciones propias en Google Colab] Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1KWDloVh-9NaxnYSaT6gerGY-0bkwldqs?usp=sharing
- ChatGPT (2025). Asistencia en redacción, ejemplos y mejoras de documentación. OpenAI. Recuperado el 26 de agosto de 2025, de https://chat.openai.com/
