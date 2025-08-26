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
- Pandas documentation — pandas 2.3.2 documentation. (s/f). Pydata.org. Recuperado el 26 de agosto de 2025, de https://pandas.pydata.org/docs/
- [Ejecuciones propias en Google Colab] Google colab. (s/f). Google.com. Recuperado el 26 de agosto de 2025, de https://colab.research.google.com/drive/1KWDloVh-9NaxnYSaT6gerGY-0bkwldqs?usp=sharing