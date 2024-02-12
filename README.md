![Static Badge](https://img.shields.io/badge/PowerBI-gray?style=flat&logo=powerbi)
![Static Badge](https://img.shields.io/badge/Python-gray?style=flat&logo=python)
![Static Badge](https://img.shields.io/badge/-Pandas-gray?style=flat&logo=pandas)
![Static Badge](https://img.shields.io/badge/-Matplotlib-gray?style=flat&logo=matplotlib)
![Static Badge](https://img.shields.io/badge/-Seaborn-gray?style=flat&logo=seaborn)
![Static Badge](https://img.shields.io/badge/Visual_Studio_Code-gray?style=flat&logo=visual%20studio%20code&logoColor=white)

## **Proyecto Individual** - 02-Siniestros Viales en CABA con víctimas fatales - (2016-2021) 

## **Introducción**⚠️ 🚧
Este proyecto se llevó a cabo en el rol simulado de un Analista de Datos dentro de una consultora, con el propósito de desarrollar un análisis de datos requerido por el `Observatorio de Movilidad y Seguridad Vial (OMSV)`, perteneciente a la Secretaría de Transporte del Gobierno de la Ciudad Autónoma de Buenos Aires (CABA).

El objetivo principal del proyecto es proporcionar información fundamentada que facilite la toma de decisiones a las partes pertinentes, con el fin de prevenir accidentes viales, aumentar la seguridad en las carreteras y reducir el número de accidentes fatales en la Ciudad de Buenos Aires.

Las tasas de mortalidad asociadas con accidentes de tráfico son indicadores críticos de la seguridad vial en una determinada área. Estas tasas se suelen calcular como el número de fallecimientos por cada cierto número de habitantes o por cada cierta cantidad de vehículos registrados. La reducción de estas tasas es un objetivo fundamental para mejorar la seguridad vial y proteger la vida de los ciudadanos en la urbe.

Para lograr este propósito, se emplean datos iniciales obtenidos de un conjunto de datos que contiene información sobre los accidentes mortales de tráfico en la Ciudad de Buenos Aires durante los años 2016-2021. Estos datos están disponibles al público en la página oficial de CABA y pueden ser accedidos desde allí.
[Datos oficiales](https://data.buenosaires.gob.ar/dataset/victimas-siniestros-viales)

## **Situación de la problemática**

Los incidentes viales, conocidos también como accidentes de tráfico o de tránsito, son sucesos que involucran vehículos en las vías públicas y pueden tener distintas causas, como colisiones entre automóviles, motocicletas, bicicletas o peatones, atropellos, choques contra objetos fijos o volcaduras de vehículos. Estos eventos pueden resultar en daños materiales, lesiones graves o incluso la pérdida de vidas.

En Argentina, cada año se registran alrededor de 4.000 muertes por siniestros viales. Aunque muchas jurisdicciones han logrado reducir la cantidad de accidentes de tránsito, estos siguen siendo la principal causa de muertes violentas en el país. De acuerdo con los informes del Sistema Nacional de Información Criminal (SNIC) del Ministerio de Seguridad de la Nación, entre 2018 y 2022 se reportaron 19.630 muertes por siniestros viales en todo el país, lo que equivale a un promedio de 11 personas fallecidas por día debido a accidentes de tránsito.

Buenos Aires, la capital y ciudad más poblada de la República Argentina, tiene una superficie de poco más de 200 km2 y un perímetro de 60 km. La ciudad está dividida en quince comunas, con una densidad de población que supera los 15.000 habitantes por kilómetro cuadrado. Las zonas centro y norte son las áreas con mayor densidad poblacional. Según el Censo de 2022, la población de la ciudad es de 3 120 612 habitantes.

Solo en el año 2022, se contabilizaron 3.828 muertes fatales en siniestros viales en Buenos Aires. Los expertos señalan que en Argentina, la probabilidad de que una persona fallezca en un accidente de tránsito es dos o tres veces mayor que en un incidente delictivo de inseguridad. Esta situación subraya la urgencia de abordar de manera efectiva la seguridad vial en el país, especialmente en áreas urbanas densamente pobladas como Buenos Aires.

### Explicación del proyecto

Para este proyecto se trabajó con la **Bases de Víctimas Fatales en Siniestros Viales** que se encuentra en formato de Excel y contiene dos pestañas de datos:

 * **HECHOS**: que contiene una fila de hecho con id único y las variables temporales, espaciales y participantes asociadas al mismo.

 * **VICTIMAS**: contiene una fila por cada víctima de los hechos y las variables edad, sexo y modo de desplazamiento asociadas a cada víctima. Se vincula a los HECHOS mediante el id del hecho.

Asimismo, se utilizo el dataset complementario llamado **lesiones**, y se realizo un proceso de **web scrapping** para la obtención de datasets que complementen la información obteniendo la data de accidentes del año 2023.

### Proceso de ETL (Extracción, limpieza y carga de datos)
El proceso de extracción de datos se realiza en los datasets **Bases de Víctimas Fatales en Siniestros Viales** y **lesiones** en los que se realiza una extracción de la tabla HECHOS y VICTIMAS que se encontraban en hojas independientes dentro de los archivos tipo xlsx a los cuales se realizaron un merge para poder agrupar toda esa información en dos dataframes. En el caso, de los archivos **siniestros** y **mujeres** se obtuvieron mediante un proceso web scrapping.
En la etapa de transformación y limpieza de datos de estos cuatro datasets distintos se obtuvieron archivos finales ubicados en la ruta EDA/Datasets 

### Proceso de EDA (Análisis Exploratorio de los datos)
Una vez que los datos se encontraron limpios se procedio a buscar valores nulos y poder eliminarlos de las columnas (Cruce y
Direccion_Normalizada) asi como también la eliminación de las valores duplicados que se encontraban en el dataframe.
Se procedio a cambiar el tipo de dato de ciertas columnas como:
- Edad a tipo entero
- Victima, Tipo_calle, Comuna, Acusado, Fecha, Rol y Sexo a tipo categoria
Como último paso para el tratamiento de los datos se busco reemplazar SD por valores que cobren un mayor significado de acuerdo a la columna que pertenecieran

-`Análisis de lugares con mayor incidencia a accidentes de tránsito:` 
En el transcurso del tiempo, se halla una alta tendencia en los accidentes de tránsito con víctimas fatales a desarrollarse en lugares como las avenidas, esto puede suponerse a una mala señalización por la zona debido a la alta confluencia vehicular, teniendo como principales partes **auto-peaton**
![Distribución](images\dist_calle.png)

-`Análisis de edad participativos:` 
Se presenta en la gráfica una clara diferencia de personas participes en accidentes de tránsito siendo la de mayor influencia la de genero masculino en el rango de edades de 21-30 y el segundo de 31-40 esto a lo mejor se debe a una mayor población masculina por la zona 
![Distribuxión](images\Dist_edad.png)

### Indicadores de Rendimiento Clave KPI

Una vez finalizado el Análisis Exploratorio, se utiliza el dataset resultante [Homicidios](EDA\Datasets\data_homicidios.csv); para trabajar en la herramienta de visualización de datos PowerBI a fin de obtener los KPI (Indicadores de Rendimiento Clave) y un `dashboard` de presentación del informe y Visualización de datos.

![KPI](images\kpi.png)

 - **Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior**

Se define la tasa de homicidios en siniestros viales como el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico. Su fórmula es: (Número de homicidios en siniestros viales / Población total) * 100,000

Esto se encuentra en el archivo EDA\EDA.ipynb desarrollado un dataframe mediante la función `calcular_kpi` en donde se obtiene los resultados del kpi por cada semestre de cada año 

 - **Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior**

Se define la cantidad de accidentes mortales de motociclistas en siniestros viales como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal. Su fórmula para medir la evolución de los accidentes mortales con víctimas en moto es: (Número de accidentes mortales con víctimas en moto en el año anterior - Número de accidentes mortales con víctimas en moto en el año actual) / (Número de accidentes mortales con víctimas en moto en el año anterior) * 100


 - **Reducir un 20% de accidentes fatales según el tipo de calle**

Se define la cantidad de accidentes fatales en siniestros viales como el número absoluto de accidentes fatales que circulaban de distintos generos en los que estuvieron involucradas víctimas que circulaban en un determinado espacio. 

## **Conclusiones**

A partir del análisis exploratorio de los datos y su posterior visualización y comportamiento de los datos en el dashboard realizado en PowerBI, se puede concluir lo siguiente:
- Existe una alta cantidad de accidentes en la zona de la comuna 2 sobretodo en los espacios de avenidas.
- Las víctimas que salieron afectadas mayormente se encontraban en una moto.
- Las víctimas son un 77.2% de víctimas masculinas con mayor influencia en el rango etario de 21-30 años y en segundo orden de 31-40, habiendo una mayor cantidad de accidentes en el año 2018.
- Se observo un patrón en relación con la variable Edad, Hora y Sexo. Donde los Masculinos de entre 20 a 40 años y en los horarios de entrada y salida laboral o para el caso de los fines de semana en horas de salidas nocturnas.
- En cuanto a el lugar donde se producen los siniestros, las Avenidas a lo largo de los años han sido los espacios de mayor cantidad de siniestros; y en Cruce mayor a las calles. 

Asi se concluye que deberían mejorarse las señales y controles en las Avenidas sobre todo en las comunas 4 de CABA. Que podrían generarse campañas de prevención dirigidas a los Masculinos de entre 20 y 40 años.