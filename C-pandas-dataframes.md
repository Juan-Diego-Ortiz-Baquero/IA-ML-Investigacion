# Pandas - Creación y manipulación de DataFrames y Series

## 1. Crear DataFrames y Series

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

# Desde lista de listas
df2 = pd.DataFrame([[10, 20], [30, 40]], columns=['X', 'Y'])
print(df2)
# Resultado:
#     X   Y
# 0  10  20
# 1  30  40
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
```

---

## 2. Cargar datos desde archivo

```python
# Leer CSV
df = pd.read_csv('archivo.csv')
print(df.head()) #Ver las primeras filas

# Leer Excel
df_excel = pd.read_excel('archivo.xlsx')
print(df_excel.head())
```

---

## 3. Selección de columnas y filas

## Seleccionar columnas

```python
# Una Columna
print(df['A'])

# Varias Columnas
print(df[['A', 'B']])
```

### Seleccionar filas (por índice, posición o condición)

```python
# Primera fila por posición
print(df.iloc[0])
# Resultado
# A    1
# B    a
# Name: 0, dtype: object

# Fila por etiqueta (Si hay índices personalizados)
print(df.iloc[0])
# Resultado
# A    1
# B    a
# Name: 0, dtype: object

# Filas por condición
print(df[df['A'] > 1])
# Resultado
#    A  B
# 1  2  b
# 2  3  c
```

---

## 4. Tipos de datos y conversión

```python
print(df.dtypes) # Ver tipo de cada columna
# Resultado
# A     int64
# B    object
# dtype: object

# Covertir tipo de columna
df['A'] = df['A'].astype(float)
print(df.dtypes)
# Resultado
# A    float64
# B     object
# dtype: object
```

---

## Fuentes

- Pandas documentation — pandas 2.3.2 documentation. (s/f). Pydata.org. Recuperado el 26 de agosto de 2025, de https://pandas.pydata.org/docs