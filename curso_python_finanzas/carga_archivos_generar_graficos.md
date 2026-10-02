<div align="center">

<h1> 📚 Cómo cargar un archivo y graficar con Python </h1>

*Guía rápida usando **pandas** para cargar datos y **matplotlib** para graficar.s*

</div>


<br>

## Índice

- [Índice](#índice)
- [1. Cargar el archivo](#1-cargar-el-archivo)
- [2. Graficar según la info](#2-graficar-según-la-info)
- [Otros tipos de gráfico comunes](#otros-tipos-de-gráfico-comunes)
- [Tips clave](#tips-clave)

<br>


## 1. Cargar el archivo

```python
import pandas as pd

# CSV
df = pd.read_csv("archivo.csv")

# Excel
df = pd.read_excel("archivo.xlsx")

# Ver las primeras filas para entender la estructura
print(df.head())
print(df.columns)
```

## 2. Graficar según la info

```python
import matplotlib.pyplot as plt

# Ejemplo: gráfico de línea
plt.plot(df["fecha"], df["ventas"])
plt.xlabel("Fecha")
plt.ylabel("Ventas")
plt.title("Ventas en el tiempo")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

## Otros tipos de gráfico comunes

```python
# Barras
plt.bar(df["categoria"], df["valor"])

# Dispersión
plt.scatter(df["x"], df["y"])

# Histograma
plt.hist(df["columna"], bins=20)
```

## Tips clave

- `df.head()` y `df.info()` te ayudan a saber qué columnas y tipos de datos tenés antes de graficar.
- Si las fechas no se leen bien, usá `pd.read_csv("archivo.csv", parse_dates=["fecha"])`.
- Para guardar el gráfico en vez de solo mostrarlo: `plt.savefig("grafico.png")`.


<br>

---

<div align="center">

<h2> Developer </h2>

<h3> Felipe Andrés Ruiz Rojas </h3>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-linkedin.com%2Fin%2Fruizrojasfel-blue)](https://www.linkedin.com/in/ruizrojasfel) [![Website](https://img.shields.io/badge/Website-felruiz--dev.netlify.app-lightblue)](https://felruiz-dev.netlify.app/)

Copyright © 2026 Fel Ruiz
</div>
