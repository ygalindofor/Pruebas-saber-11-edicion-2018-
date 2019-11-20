# Analisis de los resultados de las pruebas saber 11 edicion 2018 a traves de tecnicas de mineria de datos

primero se importan las librerias necesrias

### import libs

```python
import pandas as pd
```

Luego para la lectura del dataset a traves de la libreria pandas como pd lo podemos leer, ya que en este caso es un .csv se lee con pd.read_csv
Fuera un .json o otro tipo de dataset la sintaxis no es que cambie mucho

#### json       pd.read_json()
#### excel      pd.read_excel()
#### sql        pd.read_sql()

hay que tener encuenta con que caracter estan separados los datos en este caso es con , y por ello se añade la sintaxis sep=','

low_memory=False    Es un parametro que funciona para la limpieza de los datos

```python
url = 'Saber_11__2018-2.csv'
pruebasSaber11_df = pd.read_csv(url, sep=',', low_memory=False)


```

```python
pruebasSaber11_df.head(10)
```

```python
pruebasSaber11_df = pruebasSaber11_df.iloc[:, [13,16, 22, 24, 64]]
pruebasSaber11_df.head(10)
```
