# Analisis de los resultados de las pruebas saber 11 edicion 2018 a traves de
tecnicas de mineria de datos

primero se importan las librerias necesarias

### import libs

```python
import pandas as pd
```

### Lectura del Dataset

Luego para la lectura del dataset a traves de la libreria pandas como pd lo
podemos leer, ya que en este caso es un .csv se lee con pd.read_csv

Fuera un
.json o otro tipo de dataset la sintaxis no es que cambie mucho

### json       pd.read_json()
### excel      pd.read_excel()
### sql
pd.read_sql()

hay que tener encuenta con que caracter estan separados los datos en este caso
es con , y por ello se añade la sintaxis sep=','

low_memory=False    Es un parametro que funciona para la limpieza de los datos

```python
url = 'Saber_11__2018-2.csv'
pruebasSaber11_df = pd.read_csv(url, sep=',', low_memory=False)


```

a traves de df.head(n) puedo mostrar las primeras filas del dataset

```python
pruebasSaber11_df.head(10)
```

### Definicion de variables o categorias

Con .iloc es posible escoger unicamente las columnas o variables con las que se
desea trabajar, haciendo esto a traves de la ubicacion de las variables
primeramente seleccionando con : todas las filas y ya luego las columnas. Por
ejemplo en este caso la variable ESTU_MCPIO_RESIDE se encuentra en la posicion
13.

```python
pruebasSaber11_df = pruebasSaber11_df.iloc[:, [13,16, 22, 24, 64]]
pruebasSaber11_df.head(10)
```

# Seleccion de renglones

Se puede hacer la seleccion de renglones en los que se encuentre el municipio de
Soacha 
A traves de loc seleccionandolo en este caso por nombre a diferencia de
iloc que es por ubicacion



```python
pruebasSaber11_df.set_index("ESTU_MCPIO_RESIDE", inplace=True)
pruebasSaber11_df.loc['SOACHA']
```
