#Analisis de los resultados de las pruebas saber 11 edicion 2018 a traves de
tecnicas de mineria de datos

####primero se importan las librerias necesarias

### import libs

```{.python .input}
import pandas as pd
```

####Luego para la lectura del dataset a traves de la libreria pandas como pd lo
podemos leer, ya que en este caso es un .csv se lee con pd.read_csv
####Fuera un
.json o otro tipo de dataset la sintaxis no es que cambie mucho

####json       pd.read_json()
####excel      pd.read_excel()
####sql
pd.read_sql()

####hay que tener encuenta con que caracter estan separados los datos en este
caso es con , y por ello se añade la sintaxis sep=','

####low_memory=False    Es un parametro que funciona para la limpieza de los
datos

```{.python .input}
url = 'Saber_11__2018-2.csv'
pruebasSaber11_df = pd.read_csv(url, sep=',', low_memory=False)


```

```{.python .input  n=9}
pruebasSaber11_df.head(10)
```

```{.json .output n=9}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>ESTU_TIPODOCUMENTO</th>\n      <th>ESTU_NACIONALIDAD</th>\n      <th>ESTU_GENERO</th>\n      <th>ESTU_FECHANACIMIENTO</th>\n      <th>PERIODO</th>\n      <th>ESTU_CONSECUTIVO</th>\n      <th>ESTU_ESTUDIANTE</th>\n      <th>ESTU_PAIS_RESIDE</th>\n      <th>ESTU_TIENEETNIA</th>\n      <th>ESTU_ETNIA</th>\n      <th>ESTU_LIMITA_MOTRIZ</th>\n      <th>ESTU_DEPTO_RESIDE</th>\n      <th>ESTU_COD_RESIDE_DEPTO</th>\n      <th>ESTU_MCPIO_RESIDE</th>\n      <th>ESTU_COD_RESIDE_MCPIO</th>\n      <th>FAMI_ESTRATOVIVIENDA</th>\n      <th>FAMI_PERSONASHOGAR</th>\n      <th>FAMI_CUARTOSHOGAR</th>\n      <th>FAMI_EDUCACIONPADRE</th>\n      <th>FAMI_EDUCACIONMADRE</th>\n      <th>FAMI_TRABAJOLABORPADRE</th>\n      <th>FAMI_TRABAJOLABORMADRE</th>\n      <th>FAMI_TIENEINTERNET</th>\n      <th>FAMI_TIENESERVICIOTV</th>\n      <th>FAMI_TIENECOMPUTADOR</th>\n      <th>FAMI_TIENELAVADORA</th>\n      <th>FAMI_TIENEHORNOMICROOGAS</th>\n      <th>FAMI_TIENEAUTOMOVIL</th>\n      <th>FAMI_TIENEMOTOCICLETA</th>\n      <th>FAMI_TIENECONSOLAVIDEOJUEGOS</th>\n      <th>FAMI_NUMLIBROS</th>\n      <th>FAMI_COMELECHEDERIVADOS</th>\n      <th>FAMI_COMECARNEPESCADOHUEVO</th>\n      <th>FAMI_COMECEREALFRUTOSLEGUMBRE</th>\n      <th>FAMI_SITUACIONECONOMICA</th>\n      <th>ESTU_DEDICACIONLECTURADIARIA</th>\n      <th>ESTU_DEDICACIONINTERNET</th>\n      <th>ESTU_HORASSEMANATRABAJA</th>\n      <th>ESTU_TIPOREMUNERACION</th>\n      <th>COLE_CODIGO_ICFES</th>\n      <th>...</th>\n      <th>COLE_NATURALEZA</th>\n      <th>COLE_CALENDARIO</th>\n      <th>COLE_BILINGUE</th>\n      <th>COLE_CARACTER</th>\n      <th>COLE_COD_DANE_SEDE</th>\n      <th>COLE_NOMBRE_SEDE</th>\n      <th>COLE_SEDE_PRINCIPAL</th>\n      <th>COLE_AREA_UBICACION</th>\n      <th>COLE_JORNADA</th>\n      <th>COLE_COD_MCPIO_UBICACION</th>\n      <th>COLE_MCPIO_UBICACION</th>\n      <th>COLE_COD_DEPTO_UBICACION</th>\n      <th>COLE_DEPTO_UBICACION</th>\n      <th>ESTU_PRIVADO_LIBERTAD</th>\n      <th>ESTU_COD_MCPIO_PRESENTACION</th>\n      <th>ESTU_MCPIO_PRESENTACION</th>\n      <th>ESTU_DEPTO_PRESENTACION</th>\n      <th>ESTU_COD_DEPTO_PRESENTACION</th>\n      <th>PUNT_LECTURA_CRITICA</th>\n      <th>PERCENTIL_LECTURA_CRITICA</th>\n      <th>DESEMP_LECTURA_CRITICA</th>\n      <th>PUNT_MATEMATICAS</th>\n      <th>PERCENTIL_MATEMATICAS</th>\n      <th>DESEMP_MATEMATICAS</th>\n      <th>PUNT_C_NATURALES</th>\n      <th>PERCENTIL_C_NATURALES</th>\n      <th>DESEMP_C_NATURALES</th>\n      <th>PUNT_SOCIALES_CIUDADANAS</th>\n      <th>PERCENTIL_SOCIALES_CIUDADANAS</th>\n      <th>DESEMP_SOCIALES_CIUDADANAS</th>\n      <th>PUNT_INGLES</th>\n      <th>PERCENTIL_INGLES</th>\n      <th>DESEMP_INGLES</th>\n      <th>PUNT_GLOBAL</th>\n      <th>PERCENTIL_GLOBAL</th>\n      <th>ESTU_NSE_ESTABLECIMIENTO</th>\n      <th>ESTU_INSE_INDIVIDUAL</th>\n      <th>ESTU_NSE_INDIVIDUAL</th>\n      <th>ESTU_ESTADOINVESTIGACION</th>\n      <th>ESTU_GENERACION-E</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>CR</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>10/06/2002</td>\n      <td>20182</td>\n      <td>SB11201820408513</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>ATLANTICO</td>\n      <td>08</td>\n      <td>SOLEDAD</td>\n      <td>08758</td>\n      <td>Estrato 2</td>\n      <td>7 a 8</td>\n      <td>Cuatro</td>\n      <td>No sabe</td>\n      <td>No sabe</td>\n      <td>Es vendedor o trabaja en atenci\u00f3n al p\u00fablico</td>\n      <td>Es vendedor o trabaja en atenci\u00f3n al p\u00fablico</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>26 A 100 LIBROS</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>1 o 2 veces por semana</td>\n      <td>Igual</td>\n      <td>30 minutos o menos</td>\n      <td>M\u00e1s de 3 horas</td>\n      <td>0</td>\n      <td>No</td>\n      <td>122432</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>ACAD\u00c9MICO</td>\n      <td>108001002924</td>\n      <td>INST. EDUC. DIST. PARA EL DESARROLLO HUMANO  M...</td>\n      <td>S</td>\n      <td>URBANO</td>\n      <td>MA\u00d1ANA</td>\n      <td>8001</td>\n      <td>BARRANQUILLA</td>\n      <td>8</td>\n      <td>ATLANTICO</td>\n      <td>N</td>\n      <td>8001</td>\n      <td>BARRANQUILLA</td>\n      <td>ATLANTICO</td>\n      <td>8</td>\n      <td>63</td>\n      <td>84</td>\n      <td>3</td>\n      <td>69</td>\n      <td>95</td>\n      <td>3</td>\n      <td>54</td>\n      <td>67</td>\n      <td>2</td>\n      <td>57</td>\n      <td>76</td>\n      <td>3</td>\n      <td>65.0</td>\n      <td>90</td>\n      <td>A2</td>\n      <td>305</td>\n      <td>85</td>\n      <td>2.0</td>\n      <td>53.169929</td>\n      <td>NSE3</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>22/10/2000</td>\n      <td>20182</td>\n      <td>SB11201820541500</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>CORDOBA</td>\n      <td>23</td>\n      <td>LORICA</td>\n      <td>23417</td>\n      <td>Estrato 1</td>\n      <td>5 a 6</td>\n      <td>Dos</td>\n      <td>Secundaria (Bachillerato) completa</td>\n      <td>Primaria completa</td>\n      <td>Trabaja por cuenta propia (por ejemplo plomero...</td>\n      <td>Trabaja en el hogar, no trabaja o estudia</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>11 A 25 LIBROS</td>\n      <td>Nunca o rara vez comemos eso</td>\n      <td>1 o 2 veces por semana</td>\n      <td>1 o 2 veces por semana</td>\n      <td>Mejor</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>0</td>\n      <td>No</td>\n      <td>28704</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>ACAD\u00c9MICO</td>\n      <td>123417001632</td>\n      <td>IE ANTONIO DE LA TORRE Y MIRANDA</td>\n      <td>S</td>\n      <td>URBANO</td>\n      <td>UNICA</td>\n      <td>23417</td>\n      <td>LORICA</td>\n      <td>23</td>\n      <td>CORDOBA</td>\n      <td>N</td>\n      <td>23417</td>\n      <td>LORICA</td>\n      <td>CORDOBA</td>\n      <td>23</td>\n      <td>54</td>\n      <td>54</td>\n      <td>3</td>\n      <td>50</td>\n      <td>48</td>\n      <td>2</td>\n      <td>50</td>\n      <td>53</td>\n      <td>2</td>\n      <td>40</td>\n      <td>28</td>\n      <td>1</td>\n      <td>48.0</td>\n      <td>46</td>\n      <td>A1</td>\n      <td>242</td>\n      <td>46</td>\n      <td>2.0</td>\n      <td>45.062853</td>\n      <td>NSE2</td>\n      <td>PUBLICAR</td>\n      <td>GENERACION E - GRATUIDAD</td>\n    </tr>\n    <tr>\n      <th>2</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>19/12/2001</td>\n      <td>20182</td>\n      <td>SB11201820208467</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>VALLE</td>\n      <td>76</td>\n      <td>CALI</td>\n      <td>76001</td>\n      <td>Estrato 2</td>\n      <td>1 a 2</td>\n      <td>Dos</td>\n      <td>No sabe</td>\n      <td>T\u00e9cnica o tecnol\u00f3gica incompleta</td>\n      <td>No sabe</td>\n      <td>Es vendedor o trabaja en atenci\u00f3n al p\u00fablico</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>26 A 100 LIBROS</td>\n      <td>1 o 2 veces por semana</td>\n      <td>3 a 5 veces por semana</td>\n      <td>1 o 2 veces por semana</td>\n      <td>Mejor</td>\n      <td>30 minutos o menos</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>0</td>\n      <td>No</td>\n      <td>112466</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>T\u00c9CNICO/ACAD\u00c9MICO</td>\n      <td>276001010994</td>\n      <td>FRANCISCO JOSE LLOREDA MERA - SEDE PRINCIPAL</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>MA\u00d1ANA</td>\n      <td>76001</td>\n      <td>CALI</td>\n      <td>76</td>\n      <td>VALLE</td>\n      <td>N</td>\n      <td>76001</td>\n      <td>CALI</td>\n      <td>VALLE</td>\n      <td>76</td>\n      <td>59</td>\n      <td>72</td>\n      <td>3</td>\n      <td>43</td>\n      <td>28</td>\n      <td>2</td>\n      <td>46</td>\n      <td>40</td>\n      <td>2</td>\n      <td>45</td>\n      <td>43</td>\n      <td>2</td>\n      <td>47.0</td>\n      <td>42</td>\n      <td>A-</td>\n      <td>241</td>\n      <td>45</td>\n      <td>2.0</td>\n      <td>44.806936</td>\n      <td>NSE2</td>\n      <td>PUBLICAR</td>\n      <td>GENERACION E - GRATUIDAD</td>\n    </tr>\n    <tr>\n      <th>3</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>20/10/2000</td>\n      <td>20182</td>\n      <td>SB11201820514682</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>BOYACA</td>\n      <td>15</td>\n      <td>TUNJA</td>\n      <td>15001</td>\n      <td>Estrato 3</td>\n      <td>3 a 4</td>\n      <td>Tres</td>\n      <td>No sabe</td>\n      <td>Educaci\u00f3n profesional completa</td>\n      <td>No sabe</td>\n      <td>Es due\u00f1o de un negocio peque\u00f1o (tiene pocos em...</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>M\u00c1S DE 100 LIBROS</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Igual</td>\n      <td>30 minutos o menos</td>\n      <td>M\u00e1s de 3 horas</td>\n      <td>0</td>\n      <td>No</td>\n      <td>134692</td>\n      <td>...</td>\n      <td>NO OFICIAL</td>\n      <td>A</td>\n      <td>-</td>\n      <td>ACAD\u00c9MICO</td>\n      <td>315001003772</td>\n      <td>INSTITUCION EDUCATIVA URIBESCO - SEDE PRINCIPAL</td>\n      <td>S</td>\n      <td>URBANO</td>\n      <td>MA\u00d1ANA</td>\n      <td>15001</td>\n      <td>TUNJA</td>\n      <td>15</td>\n      <td>BOYACA</td>\n      <td>N</td>\n      <td>15001</td>\n      <td>TUNJA</td>\n      <td>BOYACA</td>\n      <td>15</td>\n      <td>61</td>\n      <td>79</td>\n      <td>3</td>\n      <td>60</td>\n      <td>78</td>\n      <td>3</td>\n      <td>60</td>\n      <td>84</td>\n      <td>3</td>\n      <td>67</td>\n      <td>94</td>\n      <td>3</td>\n      <td>63.0</td>\n      <td>86</td>\n      <td>A2</td>\n      <td>310</td>\n      <td>87</td>\n      <td>3.0</td>\n      <td>73.630225</td>\n      <td>NSE4</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>4</th>\n      <td>CC</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>16/11/1998</td>\n      <td>20182</td>\n      <td>SB11201820306251</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>BOGOTA</td>\n      <td>11</td>\n      <td>BOGOT\u00c1 D.C.</td>\n      <td>11001</td>\n      <td>Estrato 2</td>\n      <td>7 a 8</td>\n      <td>Tres</td>\n      <td>No sabe</td>\n      <td>No sabe</td>\n      <td>No aplica</td>\n      <td>Trabaja en el hogar, no trabaja o estudia</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>M\u00c1S DE 100 LIBROS</td>\n      <td>1 o 2 veces por semana</td>\n      <td>1 o 2 veces por semana</td>\n      <td>3 a 5 veces por semana</td>\n      <td>Igual</td>\n      <td>30 minutos o menos</td>\n      <td>Entre 1 y 3 horas</td>\n      <td>Menos de 10 horas</td>\n      <td>No</td>\n      <td>80051</td>\n      <td>...</td>\n      <td>NO OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>T\u00c9CNICO/ACAD\u00c9MICO</td>\n      <td>311001050023</td>\n      <td>COLEGIO DE EDUCACI\u00d3N T\u00c9CNICA Y ACAD\u00c9MICA CELES...</td>\n      <td>S</td>\n      <td>URBANO</td>\n      <td>COMPLETA</td>\n      <td>11001</td>\n      <td>BOGOT\u00c1 D.C.</td>\n      <td>11</td>\n      <td>BOGOTA</td>\n      <td>N</td>\n      <td>11001</td>\n      <td>BOGOT\u00c1 D.C.</td>\n      <td>BOGOTA</td>\n      <td>11</td>\n      <td>56</td>\n      <td>64</td>\n      <td>3</td>\n      <td>51</td>\n      <td>53</td>\n      <td>3</td>\n      <td>48</td>\n      <td>45</td>\n      <td>2</td>\n      <td>49</td>\n      <td>55</td>\n      <td>2</td>\n      <td>56.0</td>\n      <td>71</td>\n      <td>A1</td>\n      <td>257</td>\n      <td>57</td>\n      <td>3.0</td>\n      <td>49.391007</td>\n      <td>NSE2</td>\n      <td>PUBLICAR</td>\n      <td>GENERACION E - GRATUIDAD</td>\n    </tr>\n    <tr>\n      <th>5</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>F</td>\n      <td>14/03/2000</td>\n      <td>20182</td>\n      <td>SB11201820231418</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>Si</td>\n      <td>Otro grupo \u00e9tnico minoritario</td>\n      <td>-</td>\n      <td>CHOCO</td>\n      <td>27</td>\n      <td>EL LITORAL DEL SAN JUAN</td>\n      <td>27250</td>\n      <td>-</td>\n      <td>9 o m\u00e1s</td>\n      <td>Dos</td>\n      <td>-</td>\n      <td>-</td>\n      <td>No aplica</td>\n      <td>No aplica</td>\n      <td>-</td>\n      <td>-</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>-</td>\n      <td>-</td>\n      <td>Igual</td>\n      <td>-</td>\n      <td>-</td>\n      <td>M\u00e1s de 30 horas</td>\n      <td>No</td>\n      <td>114181</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>T\u00c9CNICO/ACAD\u00c9MICO</td>\n      <td>327361060015</td>\n      <td>IE IND\u00cdGENA GERARDO CHIRIPUA VALENCIA - SEDE P...</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>MA\u00d1ANA</td>\n      <td>27250</td>\n      <td>EL LITORAL DEL SAN JUAN</td>\n      <td>27</td>\n      <td>CHOCO</td>\n      <td>N</td>\n      <td>76109</td>\n      <td>BUENAVENTURA</td>\n      <td>VALLE</td>\n      <td>76</td>\n      <td>28</td>\n      <td>1</td>\n      <td>1</td>\n      <td>35</td>\n      <td>10</td>\n      <td>1</td>\n      <td>36</td>\n      <td>10</td>\n      <td>1</td>\n      <td>37</td>\n      <td>19</td>\n      <td>1</td>\n      <td>37.0</td>\n      <td>10</td>\n      <td>A-</td>\n      <td>171</td>\n      <td>4</td>\n      <td>2.0</td>\n      <td>30.516627</td>\n      <td>NSE1</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>6</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>21/11/2001</td>\n      <td>20182</td>\n      <td>SB11201820084292</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>Si</td>\n      <td>-</td>\n      <td>-</td>\n      <td>LA GUAJIRA</td>\n      <td>44</td>\n      <td>URIBIA</td>\n      <td>44847</td>\n      <td>Sin Estrato</td>\n      <td>7 a 8</td>\n      <td>Tres</td>\n      <td>Secundaria (Bachillerato) incompleta</td>\n      <td>Secundaria (Bachillerato) incompleta</td>\n      <td>No aplica</td>\n      <td>Trabaja en el hogar, no trabaja o estudia</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>11 A 25 LIBROS</td>\n      <td>1 o 2 veces por semana</td>\n      <td>1 o 2 veces por semana</td>\n      <td>Nunca o rara vez comemos eso</td>\n      <td>Igual</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>30 minutos o menos</td>\n      <td>0</td>\n      <td>No</td>\n      <td>144220</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>-</td>\n      <td>T\u00c9CNICO/ACAD\u00c9MICO</td>\n      <td>244847001344</td>\n      <td>INSTITUCI\u00c0N ETNOEDUCATIVA RURAL INTERNADO DE N...</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>MA\u00d1ANA</td>\n      <td>44847</td>\n      <td>URIBIA</td>\n      <td>44</td>\n      <td>LA GUAJIRA</td>\n      <td>N</td>\n      <td>44847</td>\n      <td>URIBIA</td>\n      <td>LA GUAJIRA</td>\n      <td>44</td>\n      <td>45</td>\n      <td>24</td>\n      <td>2</td>\n      <td>49</td>\n      <td>46</td>\n      <td>2</td>\n      <td>45</td>\n      <td>35</td>\n      <td>2</td>\n      <td>33</td>\n      <td>9</td>\n      <td>1</td>\n      <td>50.0</td>\n      <td>53</td>\n      <td>A1</td>\n      <td>218</td>\n      <td>29</td>\n      <td>1.0</td>\n      <td>38.754034</td>\n      <td>NSE1</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>7</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>20/06/2001</td>\n      <td>20182</td>\n      <td>SB11201820546789</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>ATLANTICO</td>\n      <td>08</td>\n      <td>PUERTO COLOMBIA</td>\n      <td>08573</td>\n      <td>Sin Estrato</td>\n      <td>5 a 6</td>\n      <td>Dos</td>\n      <td>Secundaria (Bachillerato) completa</td>\n      <td>Secundaria (Bachillerato) completa</td>\n      <td>Es due\u00f1o de un negocio grande, tiene un cargo ...</td>\n      <td>Trabaja en el hogar, no trabaja o estudia</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>0 A 10 LIBROS</td>\n      <td>Nunca o rara vez comemos eso</td>\n      <td>3 a 5 veces por semana</td>\n      <td>Nunca o rara vez comemos eso</td>\n      <td>Igual</td>\n      <td>No leo por entretenimiento</td>\n      <td>Entre 1 y 3 horas</td>\n      <td>Menos de 10 horas</td>\n      <td>Si, en efectivo</td>\n      <td>109033</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>ACAD\u00c9MICO</td>\n      <td>208573000072</td>\n      <td>INSTITUCION EDUCATIVA EUSTORGIO SALGAR</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>MA\u00d1ANA</td>\n      <td>8573</td>\n      <td>PUERTO COLOMBIA</td>\n      <td>8</td>\n      <td>ATLANTICO</td>\n      <td>N</td>\n      <td>8001</td>\n      <td>BARRANQUILLA</td>\n      <td>ATLANTICO</td>\n      <td>8</td>\n      <td>30</td>\n      <td>1</td>\n      <td>1</td>\n      <td>37</td>\n      <td>15</td>\n      <td>2</td>\n      <td>40</td>\n      <td>20</td>\n      <td>1</td>\n      <td>40</td>\n      <td>29</td>\n      <td>1</td>\n      <td>40.0</td>\n      <td>20</td>\n      <td>A-</td>\n      <td>185</td>\n      <td>9</td>\n      <td>2.0</td>\n      <td>54.122715</td>\n      <td>NSE3</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>8</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>26/06/2001</td>\n      <td>20182</td>\n      <td>SB11201820089757</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>CALDAS</td>\n      <td>17</td>\n      <td>MARQUETALIA</td>\n      <td>17444</td>\n      <td>Estrato 2</td>\n      <td>5 a 6</td>\n      <td>Cuatro</td>\n      <td>Primaria incompleta</td>\n      <td>Secundaria (Bachillerato) incompleta</td>\n      <td>Es agricultor, pesquero o jornalero</td>\n      <td>Trabaja en el hogar, no trabaja o estudia</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>0 A 10 LIBROS</td>\n      <td>1 o 2 veces por semana</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Todos o casi todos los d\u00edas</td>\n      <td>Igual</td>\n      <td>30 minutos o menos</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>Menos de 10 horas</td>\n      <td>Si, en efectivo</td>\n      <td>174656</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>ACAD\u00c9MICO</td>\n      <td>217444000278</td>\n      <td>INSTITUCION EDUCATIVA PATIO BONITO - SEDE PRIN...</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>COMPLETA</td>\n      <td>17444</td>\n      <td>MARQUETALIA</td>\n      <td>17</td>\n      <td>CALDAS</td>\n      <td>N</td>\n      <td>17444</td>\n      <td>MARQUETALIA</td>\n      <td>CALDAS</td>\n      <td>17</td>\n      <td>50</td>\n      <td>42</td>\n      <td>2</td>\n      <td>63</td>\n      <td>86</td>\n      <td>3</td>\n      <td>57</td>\n      <td>74</td>\n      <td>3</td>\n      <td>48</td>\n      <td>53</td>\n      <td>2</td>\n      <td>59.0</td>\n      <td>80</td>\n      <td>A2</td>\n      <td>274</td>\n      <td>68</td>\n      <td>1.0</td>\n      <td>40.687267</td>\n      <td>NSE1</td>\n      <td>PUBLICAR</td>\n      <td>NO</td>\n    </tr>\n    <tr>\n      <th>9</th>\n      <td>TI</td>\n      <td>COLOMBIA</td>\n      <td>M</td>\n      <td>20/11/2000</td>\n      <td>20182</td>\n      <td>SB11201820205097</td>\n      <td>ESTUDIANTE</td>\n      <td>COLOMBIA</td>\n      <td>No</td>\n      <td>-</td>\n      <td>-</td>\n      <td>BOYACA</td>\n      <td>15</td>\n      <td>DUITAMA</td>\n      <td>15238</td>\n      <td>Estrato 1</td>\n      <td>3 a 4</td>\n      <td>Uno</td>\n      <td>Primaria incompleta</td>\n      <td>Primaria incompleta</td>\n      <td>Es agricultor, pesquero o jornalero</td>\n      <td>Trabaja como personal de limpieza, mantenimien...</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>No</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>11 A 25 LIBROS</td>\n      <td>3 a 5 veces por semana</td>\n      <td>1 o 2 veces por semana</td>\n      <td>3 a 5 veces por semana</td>\n      <td>Igual</td>\n      <td>Entre 30 y 60 minutos</td>\n      <td>30 minutos o menos</td>\n      <td>Menos de 10 horas</td>\n      <td>No</td>\n      <td>45443</td>\n      <td>...</td>\n      <td>OFICIAL</td>\n      <td>A</td>\n      <td>N</td>\n      <td>T\u00c9CNICO/ACAD\u00c9MICO</td>\n      <td>215806000236</td>\n      <td>IE TECNICO INDUSTRIAL - SEDE PRINCIPAL</td>\n      <td>S</td>\n      <td>RURAL</td>\n      <td>COMPLETA</td>\n      <td>15806</td>\n      <td>TIBASOSA</td>\n      <td>15</td>\n      <td>BOYACA</td>\n      <td>N</td>\n      <td>15238</td>\n      <td>DUITAMA</td>\n      <td>BOYACA</td>\n      <td>15</td>\n      <td>43</td>\n      <td>19</td>\n      <td>2</td>\n      <td>51</td>\n      <td>53</td>\n      <td>3</td>\n      <td>50</td>\n      <td>55</td>\n      <td>2</td>\n      <td>50</td>\n      <td>59</td>\n      <td>2</td>\n      <td>48.0</td>\n      <td>43</td>\n      <td>A1</td>\n      <td>242</td>\n      <td>46</td>\n      <td>2.0</td>\n      <td>32.688767</td>\n      <td>NSE1</td>\n      <td>PUBLICAR</td>\n      <td>GENERACION E - GRATUIDAD</td>\n    </tr>\n  </tbody>\n</table>\n<p>10 rows \u00d7 83 columns</p>\n</div>",
   "text/plain": "  ESTU_TIPODOCUMENTO  ...         ESTU_GENERACION-E\n0                 CR  ...                        NO\n1                 TI  ...  GENERACION E - GRATUIDAD\n2                 TI  ...  GENERACION E - GRATUIDAD\n3                 TI  ...                        NO\n4                 CC  ...  GENERACION E - GRATUIDAD\n5                 TI  ...                        NO\n6                 TI  ...                        NO\n7                 TI  ...                        NO\n8                 TI  ...                        NO\n9                 TI  ...  GENERACION E - GRATUIDAD\n\n[10 rows x 83 columns]"
  },
  "execution_count": 9,
  "metadata": {
   "tags": []
  },
  "output_type": "execute_result"
 }
]
```

```{.python .input  n=10}
pruebasSaber11_df = pruebasSaber11_df.iloc[:, [13,16, 22, 24, 64]]
pruebasSaber11_df.head(10)
```

```{.json .output n=10}
[
 {
  "data": {
   "text/html": "<div>\n<style scoped>\n    .dataframe tbody tr th:only-of-type {\n        vertical-align: middle;\n    }\n\n    .dataframe tbody tr th {\n        vertical-align: top;\n    }\n\n    .dataframe thead th {\n        text-align: right;\n    }\n</style>\n<table border=\"1\" class=\"dataframe\">\n  <thead>\n    <tr style=\"text-align: right;\">\n      <th></th>\n      <th>ESTU_MCPIO_RESIDE</th>\n      <th>FAMI_PERSONASHOGAR</th>\n      <th>FAMI_TIENEINTERNET</th>\n      <th>FAMI_TIENECOMPUTADOR</th>\n      <th>PUNT_MATEMATICAS</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <th>0</th>\n      <td>SOLEDAD</td>\n      <td>7 a 8</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>69</td>\n    </tr>\n    <tr>\n      <th>1</th>\n      <td>LORICA</td>\n      <td>5 a 6</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>50</td>\n    </tr>\n    <tr>\n      <th>2</th>\n      <td>CALI</td>\n      <td>1 a 2</td>\n      <td>No</td>\n      <td>No</td>\n      <td>43</td>\n    </tr>\n    <tr>\n      <th>3</th>\n      <td>TUNJA</td>\n      <td>3 a 4</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>60</td>\n    </tr>\n    <tr>\n      <th>4</th>\n      <td>BOGOT\u00c1 D.C.</td>\n      <td>7 a 8</td>\n      <td>Si</td>\n      <td>No</td>\n      <td>51</td>\n    </tr>\n    <tr>\n      <th>5</th>\n      <td>EL LITORAL DEL SAN JUAN</td>\n      <td>9 o m\u00e1s</td>\n      <td>-</td>\n      <td>No</td>\n      <td>35</td>\n    </tr>\n    <tr>\n      <th>6</th>\n      <td>URIBIA</td>\n      <td>7 a 8</td>\n      <td>No</td>\n      <td>No</td>\n      <td>49</td>\n    </tr>\n    <tr>\n      <th>7</th>\n      <td>PUERTO COLOMBIA</td>\n      <td>5 a 6</td>\n      <td>Si</td>\n      <td>Si</td>\n      <td>37</td>\n    </tr>\n    <tr>\n      <th>8</th>\n      <td>MARQUETALIA</td>\n      <td>5 a 6</td>\n      <td>No</td>\n      <td>No</td>\n      <td>63</td>\n    </tr>\n    <tr>\n      <th>9</th>\n      <td>DUITAMA</td>\n      <td>3 a 4</td>\n      <td>No</td>\n      <td>No</td>\n      <td>51</td>\n    </tr>\n  </tbody>\n</table>\n</div>",
   "text/plain": "         ESTU_MCPIO_RESIDE  ... PUNT_MATEMATICAS\n0                  SOLEDAD  ...               69\n1                   LORICA  ...               50\n2                     CALI  ...               43\n3                    TUNJA  ...               60\n4              BOGOT\u00c1 D.C.  ...               51\n5  EL LITORAL DEL SAN JUAN  ...               35\n6                   URIBIA  ...               49\n7          PUERTO COLOMBIA  ...               37\n8              MARQUETALIA  ...               63\n9                  DUITAMA  ...               51\n\n[10 rows x 5 columns]"
  },
  "execution_count": 10,
  "metadata": {
   "tags": []
  },
  "output_type": "execute_result"
 }
]
```