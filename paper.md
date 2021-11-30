---
title: Participación política, confianza en instituciones y movimientos sociales explicando
  la satisfacción con la democracia en el Chile post estallido
author: "Luciano Fica, Aline Bonnefoyn Nicolas Tobar, Francisco Arevalo"
date: "3/10/2021"
output:
  html_document:
      code_folding: hide
bibliography: Entrega.bib
link-citations: yes
---
```{r setup, include=FALSE, warning=FALSE}
# Este es el chunk de setup

knitr::opts_chunk$set(cache=FALSE, # guarda renderizaciones parciales, ahorra tiempo
                      warning = FALSE, # evita publicar advertencias
                      message = FALSE) # evita publicar mensajes

Sys.setlocale("LC_ALL","ES_ES.UTF-8") # para temas de caracteres en español, recomendable

library(pacman)
p_load( dplyr,
        stargazer, 
        sjmisc, 
        sjlabelled,
        summarytools, 
        knitr,
        ggplot2,
        sjPlot,
        car,
        kableExtra, 
        sjPlot, 
        sessioninfo,
        corrplot,
        gridExtra,
        texreg,
        citr,
        install = T)
```
<div style="text-align: justify">
```{css, echo=FALSE}
pre {
  max-height: 200px;
  overflow-y: auto;
}

```


# Abstract:

El objetivo de este trabajo es relacionar la satisfacción con la democracia con una serie de variables independientes tales como: afiliación con los movimientos sociales, participación política y confianza en las instituciones. El objetivo de este trabajo es relacionar la satisfacción de la democracia con una serie de variables claves. Ordenamos por interés y por evidencia aquellas que consideramos más apropiadas para comprender la democracia en el Chile contemporáneo: afiliación a los movimientos sociales, en primer lugar, confianza en las instituciones. La pregunta que guía esta investigación es la siguiente: ¿Cómo es la relación entre la satisfacción con la democracia en Chile, durante el 2019, y la participación política, la participación en movimientos sociales y la confianza en las instituciones, considerando éstos como predictores de la primera? A partir de la base de datos del Estudio Longitudinal Social de Chile del 2019, liberada a principios del año 2021, construimos una serie de índices que nos permiten profundizar en la relación estadística entre estas variables. Presentamos que la sociedad chilena está más conforme con su democracia en tanto confían más en las instituciones de una república, como también hemos descubierto una relación negativa entre la satisfacción con la democracia y una participación política y su filiación a movimientos sociales.


# Introducción

Chile vive, actualmente, una crisis social, económica, sanitaria y política, iniciadas, primero por el Estallido Social del 18 de octubre de 2019 (en adelante, 18O), y luego por la pandemia, que actualmente padecemos. Dentro de este escenario, está en curso un proceso constituyente, iniciado a raíz del 18O y que fue canalizado, institucionalmente, por el poder político. En este contexto, se hace necesario atender a los grados de satisfacción con la democracia que muestra la población chilena, por ser una de las categorías que más influyen en la legitimación de la misma [@cereceda-marambio_satisfaccion_2017; @noauthor_latinobarometro_nodate; @sanhueza_democracia_2015], y así poder distinguir cómo la confianza en las instituciones, la participación política y la filiación con algún movimiento social, impactaron en 2019 a la satisfacción democrática y, por tanto a la legitimidad de la democracia y el poder, con el fin de comprender de mejor forma los motivos que incitaron el Estallido del 18O. En función de este objetivo, explicaremos los principales conceptos a abordar en este estudio y los antecedentes de investigaciones anteriores respecto a la problemática que intentamos abordar.
La legitimidad democrática (sinónimo de satisfacción democrática en este caso), se entiende como la validez que le da la ciudadanía al sistema político, democrático e institucional. Según @arroyo_tomarse_1996, la legitimidad democrática es una expresión de los movimientos sociales. Por otro lado, @lopez_hidalgo_reflexiones_2018 consideran la legitimidad como la aceptación social de los sistemas políticos. Uno de los indicadores para medir dicha legitimidad, es la satisfacción con la democracia, esta estima el desempeño del régimen democrático en el corto plazo @sanhueza_democracia_2015. Por otro lado, en @cereceda-marambio_satisfaccion_2017, se aborda nuestra variable dependiente considerando el quehacer político, crecimiento económico, los valores de la igualdad y la percepción de los derechos políticos civiles. @sanhueza_democracia_2015, por su parte, relacionan la satisfacción con la creencia en la democracia como el mejor sistema posible, una relación poco explorada. @gibert_confianza_2008 llevaron a cabo un estudio que relaciona la satisfacción con la democracia con la confianza social, política y en las instituciones, así como la relación de estas tres variables con el “asociacionismo”, o sea, la participación en organizaciones y asociaciones voluntarias. @del_campo_i_2017 estudiaron el impacto, en la satisfacción, del descontento con el Estado donde concluyeron que la confianza en el gobierno y la percepción de equidad social es lo que, principalmente, influye en la satisfacción democrática.
La legitimidad del sistema político, expresada tanto a partir del apoyo a la democracia como por su nivel de satisfacción; puede estar influida por la participación ciudadana en política. En este ámbito, @noauthor_idh_nodate señala que las personas que no asisten a votar son demócratas insatisfechos, además, la autora agrega que la legitimidad se mide en relación a las percepciones que tienen los ciudadanos según el apoyo al régimen.Sumado a esto, @chihu_amparan_construccion_2007 agregan que el hecho de no sentirse representados en el principal cargo de gobierno los lleva a estar insatisfechos con el modo en que funciona el mismo. La definición de participación política, en lo referente al análisis, adhiere cualquier actividad, electoral, voluntaria o involuntaria, que influya en las decisiones, agentes, capacidades y movimientos dentro del espectro del campo político representativo.
La confianza en las instituciones, es expresada como el grado de satisfacción que tiene la ciudadanía con el actuar de las instituciones. Según @gibert_confianza_2008 la confianza en las instituciones es el apoyo “difuso” al sistema político, que se expresa en favor de la democracia o el apoyo a los resultados de un gobierno y autoridades específicas. Existen factores que influyen en la confianza de las instituciones, según @morales_quiroga_evaluando_2008 un factor importante es el deterioro de la calidad de la democracia, ya que, determina la participación e identificación que tendrá la ciudadanía en las instituciones. Por otro lado, @quiroga_estallido_2020 aporta con el nivel de acercamiento con los partidos políticos, debido a que de éstos depende la identificación con el gobierno y así mismo su confianza en éste. De lo mencionado anteriormente, se podría apreciar una relación positiva entre confianza en las instituciones y satisfacción de la democracia, ya que, a mayor confianza en las instituciones, podría haber mayor satisfacción con la democracia y con el funcionamiento de los órganos que la componen y la posibilitan.
La categoría filiación con movimiento social estima la cercanía y representación de las personas con el movimiento social. Éste se entenderá como una iniciativa colectiva y autorreflexiva, que se enfoca en las acciones expresivas de las y los integrantes de la colectividad, donde las identidades y el movimiento surgen debido a la acción colectiva conscientemente coordinada; sus miembros, de manera consciente, desarrollan ataques y defensas, aislando, diferenciando y marcando fronteras y se organizan creando lazos y redes solidarias [@chihu_amparan_construccion_2007]. Se ha decidido emplear esta variable, fuera de participación política, ya que los movimientos sociales no expresan, únicamente, conflictos políticos, sino que además expresan, fundamentalmente, conflictos sociales [@chihu_amparan_construccion_2007]. En el caso del 18O, se destacan tres tipos de conflictos: por una mejor calidad de vida, cambiar los modos de vida y búsqueda de mayor legitimidad y eficacia de las instituciones estatales [@noauthor_idh_nodate].


# Objetivos e Hipótesis

En base a los antecedentes presentados y la problematización a resolver en el presente estudio, mencionaremos las hipótesis y objetivos que guiarán nuestro trabajo, orientado a mostrar la relación estadística entre los cuatro conceptos presentados anteriormente, revelando la naturaleza e intensidad presente en la correlación entre éstos y la influencia simultánea de las tres independientes en la satisfacción con la democracia.

## Objetivo general: 

Correlacionar y analizar la Satisfacción con la democracia en relación con la Participación política, la Participación en movimientos sociales y la Confianza en instituciones, tanto de forma bivariada como multivariada, en base a los datos recogidos por el Estudio Longitudinal Social de Chile [@noauthor_elsoc_nodate].

## Objetivos específicos:
1.	Relacionar la Satisfacción con la democracia con la Participación política en Chile.
2.	Relacionar la Satisfacción con la democracia y la Participación en movimientos sociales en nuestro país.
3.	Conocer la existencia de una relación entre la Satisfacción con la democracia de los/as chilenos/as y la Confianza en las instituciones.
4.	Conocer y analizar la influencia simultánea de nuestros tres conceptos predictores -Participación política, Participación en movimiento social y Confianza en instituciones- en la Satisfacción con la democracia en Chile. 

## Hipótesis derivadas de los antecedentes y objetivos específicos:
1.	En primer lugar, de los antecedentes expuestos se desprende una posible asociación negativa entre la Satisfacción con la democracia y la Participación política, lo cual se expresa, principalmente, en los altos grados de abstención en elecciones y las masivas movilizaciones en Chile durante el 2019. 
2.	Por otro lado, consideramos que debiera existir una asociación negativa entre el Grado de filiación con algún movimiento social y la Satisfacción con la democracia, en base a que, con mayores conflictos y movilización, se refleja la insatisfacción con el sistema democrático vigente. 
3.	Por último, proponemos una relación positiva entre la Satisfacción con la democracia y la Confianza en instituciones, puesto que ambas expresan la cercanía y la aceptación del funcionamiento democrático e institucional.


# Metodología

## A)	Base de datos

La base de datos utilizada corresponde al Estudio Longitudinal Social de Chile (ELSOC) del año 2019, elaborada por el Centro de Estudios de Conflicto y Cohesión Social (COES). La encuesta considera un total de 3417 personas encuestadas, y se levanta con el fin de “evaluar la manera cómo piensan, sienten y se comportan los chilenos en torno a un conjunto de temas referidos al conflicto y la cohesión social en Chile” [@noauthor_elsoc_nodate].
```{r echo=FALSE, results='hide'}
load("../project/input/data/original/ELSOC_W04_v2.01_R(1).RData")

options(scipen=999)
```

```{r}
dim(elsoc_2019)
```

## B)	Variables

Las variables de interés extraídas para el análisis corresponden a: Satisfacción con la democracia, las relativas al módulo de Frecuencia de la participación política, al Grado de acuerdo con la filiación a determinado movimiento social y el Grado de confianza en las instituciones chilenas. A continuación se especifican las preguntas de cada variable y sus categorías de respuesta junto con su valor numérico:

### a.	Variable dependiente:

Satisfacción con la democracia en Chile
●	Categorías: nada satisfecho/a (1), poco satisfecho (2), algo satisfecho/a (3), bastante satisfecho/a (4), muy satisfecho/a (5), no sabe (-888), no responde (-999).
```{r}
find_var(data = elsoc_2019,"democracia") # Y

freq(elsoc_2019$c01)
```

### b.	Variable independiente 1: 

Índice de Frecuencia de participación política
●	Dimensiones: firma carta o petición apoyando causa, asiste a marcha o manifestación pacífica, participa en huelga, usa redes sociales para opinar en temas públicos, participa en cacerolazos.
●	Categorías: nunca (1), casi nunca (2), a veces (3), frecuentemente (4), muy frecuentemente (5), no sabe (-888), no responde (-999).
```{r}
find_var(data = elsoc_2019,"politica") # X  
freq(elsoc_2019$c08_01)
freq(elsoc_2019$c08_02)
freq(elsoc_2019$c08_03)
freq(elsoc_2019$c08_04)
freq(elsoc_2019$c08_05)

```

### c.	Variable independiente 2: 
Índice de filiación con movimiento social
●	Dimensiones: siento un compromiso con este movimiento, me identifico con este movimiento, estoy de acuerdo con las acciones de este movimiento, pensar acerca del futuro de este movimiento me hace sentir esperanzado, las acciones y protestas de este movimiento pueden generar cambio social, los participantes me ven como un miembro más, la gente en general y quienes pertenecen al movimiento tienen posiciones similares.
●	Categorías: totalmente en desacuerdo (1), en desacuerdo (2), ni de acuerdo ni en desacuerdo (3), de acuerdo (4), totalmente de acuerdo (5), no sabe (-888), no responde (-999).

```{r}
find_var(data = elsoc_2019,"movimiento") # X1
freq (elsoc_2019)
freq(elsoc_2019$c21_01)
freq(elsoc_2019$c21_02)
freq(elsoc_2019$c21_03)
freq(elsoc_2019$c21_04)
freq(elsoc_2019$c21_05)
freq(elsoc_2019$c21_06)
freq(elsoc_2019$c21_07)
freq(elsoc_2019$c21_08)
freq(elsoc_2019$c21_09)
freq(elsoc_2019$c22)
freq(elsoc_2019$c23)
freq(elsoc_2019$c24)
```

### d.	Variable independiente 3: 
Índice de grado de confianza en instituciones chilenas
●	Dimensiones: el gobierno, los partidos políticos, Carabineros, sindicatos, Poder Judicial, empresas privadas, Congreso Nacional, Presidente, Fuerzas Armadas, Bomberos, medios de comunicación tradicionales, su municipalidad.
●	Categorías: nada (1), poca (2), algo (3), bastante (4), mucha (5), no sabe (-888), no responde (-999).
```{r}
find_var(data = elsoc_2019,"confianza") # X2  
freq(elsoc_2019$c05_01)
freq(elsoc_2019$c05_02)
freq(elsoc_2019$c05_03)
freq(elsoc_2019$c05_04)
freq(elsoc_2019$c05_05)
freq(elsoc_2019$c05_06)
freq(elsoc_2019$c05_07)
freq(elsoc_2019$c05_08)
freq(elsoc_2019$c05_10)
freq(elsoc_2019$c05_11)
freq(elsoc_2019$c05_12)
freq(elsoc_2019$c05_13)
```
```{r results='hide'}
## Seleccion de variables 
proc_elsoc <- elsoc_2019 %>% select(c01,
                                    c08_01,
                                    c08_02,
                                    c08_03,
                                    c08_04,
                                    c08_05,
                                    c21_01,
                                    c21_02,
                                    c21_03,
                                    c21_04,
                                    c21_05,
                                    c21_06,
                                    c21_07,
                                    c21_08,
                                    c05_01,
                                    c05_02,
                                    c05_03,
                                    c05_04,
                                    c05_05,
                                    c05_06,
                                    c05_07,
                                    c05_08,
                                    c05_10,
                                    c05_11,
                                    c05_12,
                                    c05_13)


## Obtener etiquetas de las variables 
sjlabelled::get_label(proc_elsoc)
```

Con el fin de extraer la mayor información posible de las variables, se crearon los índices en base al promedio, agrupando las dimensiones de cada variable a considerar. Por otro lado, para no alterar los resultados numéricos del análisis, se eliminaron las categorías de respuesta correspondientes a “no sabe” y “no responde” -con valores de -888 y -999, respectivamente. 

```{r results='hide'}
## Recodificacion 
proc_elsoc <- lapply(proc_elsoc[ ,1:26] , 
                     FUN = function(x) recode(x, "NaN = NA;-888=NA;-999=NA"))
proc_elsoc <- data.frame(proc_elsoc)

## Creación de índices en base al promedio
proc_elsoc <- proc_elsoc %>% rowwise() %>% mutate(media_politica = mean(c(c08_01, c08_02, c08_03, c08_04, c08_05), na.rm = T))
proc_elsoc <- proc_elsoc %>% rowwise() %>% mutate(media_movimiento = mean(c(c21_01, c21_02, c21_03, c21_04, c21_05, c21_06, c21_07, c21_08), na.rm = T))
proc_elsoc <- proc_elsoc %>% rowwise() %>% mutate(media_confianza = mean(c(c05_01, c05_02, c05_03, c05_04, c05_05, c05_06, c05_07, c05_08, c05_10, c05_11, c05_12, c05_13), na.rm = T))

```
```{r results='hide'}
#Creacion nueva base de datos con solo las 4 variables (2 variables, 2 indices)
proc_elsoc2 <- proc_elsoc %>% select("c01", "media_politica", "media_movimiento", "media_confianza" )

proc_elsoc3 <- proc_elsoc2 %>% rename("SDemocracia" = c01, 
                                      "FPPolitica" = media_politica,
                                      "MSociales" = media_movimiento,
                                      "CInstituciones" = media_confianza)

proc_elsoc3$SDemocracia <- set_label(x = proc_elsoc3$SDemocracia,label = "Satisfacción con la Democracia en Chile")
proc_elsoc3$FPPolitica <- set_label(x = proc_elsoc3$FPPolitica,label = "Frecuencia de Participación Política")
proc_elsoc3$MSociales <- set_label(x = proc_elsoc3$MSociales,label = "Afiliación a Movimiento Social")
proc_elsoc3$CInstituciones <- set_label(x = proc_elsoc3$CInstituciones,label = "Confianza en Instituciones")
```
```{r echo=FALSE, results='hide'}
## Extraer NA de la base de datos
proc_elsoc_original <-proc_elsoc # Respaldo base original
sum(is.na(proc_elsoc3)) # Cantidad NA en la base
proc_elsoc4 <-na.omit(proc_elsoc3) # Eliminar NA
dim(proc_elsoc4) # Dimensión base posterior eliminación de NA
```

A continuación, en la Tabla 1, se muestran los valores descriptivos de la variable Satisfacción con la democracia en Chile y de los índices: Frecuencia de participación política (media_politica), Grado de confianza en instituciones (media_confianza) y Grado de filiación con el movimiento social (media_movimiento).
```{r echo=FALSE}
Tabla_1 <- dfSummary(proc_elsoc4, headings=FALSE)
Tabla_1
```
## C)	Método de análisis

Con el fin de conocer la intensidad de las relaciones entre nuestra variable dependiente: Satisfacción con la democracia, y nuestros predictores: Índices de Participación política, de Filiación con movimiento social y de Confianza en instituciones, emplearemos un modelo de regresión múltiple, el cual se encargará de estimar la fuerza y tipo de relaciones existentes a través del cálculo de coeficientes de regresión para cada una de las tres relaciones. Este tipo de modelo de análisis, permite controlar estadísticamente las variables y sus correlaciones, a través de coeficientes de regresión parciales, que se minimizan la influencia de las correlaciones entre predictores o variables independientes, con el fin de que no afecten en la estimación final del modelo.


# Analisis

## 1.	Descriptivo
 
 En función de los valores expuestos en la Tabla 1, se realizará una descripción analítica de las cuatro variables seleccionadas. En primer lugar, nuestra variable dependiente -Satisfacción con la democracia- la cual va desde el valor 1 al 5 en orden creciente, muestra una media de 1.7, lo cual indica que, en promedio, las personas que respondieron la encuesta se encuentran “nada satisfechas” y “muy poco satisfechas” con el funcionamiento de la democracia en nuestro país. Por otro lado, el Índice de frecuencia de participación política posee una media de 1.5, indicando así que, en promedio, las personas encuestadas “nunca” o “casi nunca” realizan las actividades relacionadas a la participación política que consideramos en el índice. En tercer lugar, nuestro Índice de Filiación con algún movimiento social presenta una media de 3.9, lo cual implica que el promedio de las personas encuestadas se encuentra “de acuerdo” con las sentencias referentes al grado de simpatía por el movimiento. Por último, el Índice de Grado de confianza en las instituciones chilenas contiene una media de 2.1, por tanto, el promedio de la población encuestada siente “poca” confianza hacia las instituciones de nuestro país.
 
 
## 2.	Análisis de regresión Múltiple

A continuación, en la Tabla 2, se mostrarán los resultados y se hará un análisis bivariado de la relación estadística entre la variable dependiente: Satisfacción con la democracia y las variables independientes/predictores: Frecuencia de participación política, Grado de filiación con movimiento social y Grado de confianza en las instituciones.
 
```{r}
rs.1 <-lm(SDemocracia ~ FPPolitica, data=proc_elsoc4)
rs.2 <-lm(SDemocracia ~  MSociales, data=proc_elsoc4)
rs.3 <-lm(SDemocracia ~  CInstituciones, data=proc_elsoc4)
r.mult <- lm(SDemocracia ~ FPPolitica + MSociales + CInstituciones , data = proc_elsoc4)

```
```{r echo=FALSE}
sjPlot::tab_model(list(rs.1, rs.2,rs.3, r.mult), show.ci=FALSE, p.style = "stars", dv.labels = c("Modelo 1", "Modelo 2", "Modelo 3", "Módelo Múltiple"),string.pred = "Predictores", string.est = "β")
```

La frecuencia de participación política dio como coeficiente de regresión un -0.14 en el modelo 1 -modelo de regresión simple que vincula la variable dependiente solo con la variable FPPolitica-, y baja a -0.04 en el modelo múltiple -modelo que agrupa todas las variables independientes o predictores, e indica el grado de correlación entre éstas y la variable dependiente. Estas cifras muestran que por cada punto adicional en FPPolitica, en el modelo múltiple, se presenta una disminución de 0.04 -la cual es baja si nos fijamos en el valor de R2 = 0.016 ~ 0.01- en la satisfacción con la democracia. Esto significa que ambas variables se correlacionan de forma negativa, indicando que a mayor frecuencia de participación política, menor satisfacción con la democracia. Este valor se interpreta con un 95% de confianza, ya que la probabilidad de error es de p<0.05. 

Para la afiliación con movimientos sociales el coeficiente es de -0.17 en el modelo 2 y se reduce a -0.05 en el modelo múltiple. Demostrando que, por cada punto adicional en Msociales, en el modelo múltiple, disminuye un 0.05 la satisfacción con la democracia. Esta correlación, al igual que la anterior, es baja (R2 = 0.01 = 0.01) y negativa.
Para la variable de confianza en las instituciones, el coeficiente es de 0.65 en el modelo 3 y baja a un 0.63 en el modelo múltiple -cabe mencionar que es la variable que menos se altera al pasar del modelo simple al modelo múltiple. Esto implica que por cada punto adicional en CInstituciones, en el modelo múltiple, aumenta en un 0.62 la satisfacción con la democracia. Esta asociación, a diferencia de las anteriores, es positiva y alta, considerando R2 = 0.17 > 0.09 (intensidad media) y a la vez menor que 0.25 (intensidad alta). Este valor se interpreta con un 99,99% de confianza, según el margen de error de p<0.001.
Como mencionamos, se calcularon los coeficientes de regresión de las relaciones entre variables tanto en modelo de regresión simple -correlación bivariada- como en modelo de regresión multivariado -correlación entre variable dependiente y predictores simultáneamente-, resultando en que los valores del modelo múltiple diferían de los primeros. Esto ocurre debido a que en la estimación múltiple, se aplica un control estadístico que genera coeficientes de regresión parciales, ya que se minimiza la influencia de las correlaciones entre predictores o variables independientes, con el fin de que no afecten en la estimación del modelo.
A continuación, se muestra un gráfico que representa la intensidad de las asociaciones entre nuestras variables independientes -índices- y nuestra variable dependiente, reflejando de mejor manera las relaciones negativas, positivas y más o menos intensas, con el objeto de analizar los resultados y compararlos con nuestras hipótesis iniciales.

```{r}
graf.control <- plot_model(r.mult, show.values = TRUE)+ theme_sjplot()
```
```{r echo=FALSE}
ggsave("grafico.control.png", graf.control)

graf.control
```


## 3.	Resultados, Conclusiones y Limitaciones

A partir del modelo de regresión múltiple y del análisis expuesto anteriormente tenemos, en base a nuestras hipótesis planteadas al principio del informe, que:

1.	Que la relación entre Satisfacción con la democracia y el Índice de participación política, con un 95% de confianza en su estimación, es negativa y de intensidad baja, demostrando resultados a favor de la primera de nuestras hipótesis. 
2.	Que la correlación entre Satisfacción con la democracia y el Índice de filiación a algún movimiento social -en este caso, la estimación no presenta el nivel de confianza utilizado- es negativa y de intensidad baja, lo cual se muestra a favor de nuestra segunda hipótesis.
3.	Que la correlación entre Satisfacción con la democracia y el Índice de confianza en instituciones, con un 99,99% de confianza en la estimación, es positiva y alta, evidenciando resultados a favor de la última de nuestras hipótesis. 
A partir de los resultados obtenidos, cabe tener en cuenta que la intensidad baja y negativa de las correlaciones de la variable dependiente -Satisfacción con democracia- tanto con el Índice de participación política, como con el de Filiación a algún movimiento social, indicarían una influencia muy poco significativa de los predictores en la variable x. Por tanto, a pesar de la baja participación política en nuestro país desde el retorno a la democracia, y la cantidad de movilización social presente, sobre todo durante el año 2019, indicarían de forma parcial un descontento hacia el sistema democrático chileno, pudiendo existir otros factores que determinen estos niveles de insatisfacción, como se verá en las limitaciones del estudio. 
Por otro lado, los resultados indican una influencia alta y positiva del Grado de confianza en instituciones y la Satisfacción con la democracia. Esto era previsible en base a los antecedentes expuestos, sin embargo, la intensidad de la relación da cuenta de la direccionalidad y cercanía de ambas variables. Cabe destacar que esto no implica que en Chile existan altos niveles de confianza en instituciones ni satisfacción con la democracia, sino que estas variables están inherentemente relacionadas, por tanto, si aumenta o disminuye una, la otra también lo hará.
Por último, es necesario mencionar las limitaciones que comprende el estudio, siendo éstas: la capacidad de cuantificar el nivel de satisfacción de la ciudadanía, ya que los constructos ocupados para elaborar la variable son una representación que no puede abarcar la totalidad ni la naturaleza completa de una categoría tan abstracta y subjetiva. En cuanto a la variable independiente de movimientos, entendemos que es una simplificación para el contexto actual de la investigación sobre una temática y por lo tanto, una variable que podría ameritar su propio estudio de forma separada. Otra limitación es en cuanto a la dimensión temporal, ya que abarca la medición de un año -y de un año muy particular-, lo que no permite generalizar a otros periodos. Por último, debemos mencionar que no se aborda la dimensión económica como determinante de la satisfacción con la democracia, dimensión en la que existirían evidencias sobre su impacto [@noauthor_latinobarometro_nodate; @cereceda-marambio_satisfaccion_2017]. Sin embargo, hay otras evidencias que señalan que los factores económicos, principalmente en cuanto a percepción, no son necesariamente claves [@del_campo_i_2017].

# Referencias Bibliográficas




