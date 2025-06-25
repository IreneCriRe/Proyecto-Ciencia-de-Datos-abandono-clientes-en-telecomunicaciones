CIENCIA DE DATOS: EXAMEN FINAL
MD.PlantillaTexto(DOCUMENTO2 05)Esp.dot
3
TRABAJO FINAL: CIENCIA DE DATOS
INSTRUCCIONES
Realización del trabajo
Para la realización de este trabajo final deberás elaborar un archivo .Rmd dónde resolverás
cada uno de los ejercicios propuestos en este enunciado.
Entrega del trabajo
Para que la entrega se considere válida será necesario que nos envíes una carpeta comprimida
que contenga:
n El archivo .csv dónde se encuentran los datos que utilizarás para la realización
de los ejercicios y que se adjunta en la sección del trabajo final.
n El archivo. Rmd dónde habrás realizado cada uno de los ejercicios propuestos
en este enunciado.
n El archivo .html generado al ejecutar el archivo .Rmd mediante knit
4
TRABAJO FINAL: CIENCIA DE DATOS
IMPORTANTE:
n Si el trabajo NO se entrega siguiendo las instrucciones planteadas en este enunciado,
quedará suspendido automáticamente.
n 1 PUNTO de la valoración final del trabajo corresponderá a:
¨ La presentación, limpieza y legibilidad del documento
¨ Las explicaciones generadas
¨ La forma en la que se han empleado las herramientas y conceptos aprendidos
durante el curso.
Además, esta puntuación sólo se podrá tener en cuenta si:
¨ Se han realizado todos los ejercicios propuestos
¨ La forma de envío y realización del ejercicio coincide con las indicadas al
principio de este enunciado.
En caso contrario, la valoración siempre será 0.
5
TRABAJO FINAL: CIENCIA DE DATOS
EJERCICIO 1 – ANÁLISIS EXPLORATORIO
En primer lugar, será necesario que crees un archivo. Rmd dónde:
1. Importarás las librerías necesarias para el desarrollo del trabajo.
2. Cargarás los datos del archivo .csv en un dataframe al que llamarás:
churn_data
Análisis y preparación de los datos
Para este primer apartado será necesario que:
n Omitas los valores nulos del conjunto de datos.
n Utilices la función summary() para visualizar un resumen del conjunto de
datos.
n Haciendo uso de las opciones de formato del archivo .Rmd deberás:
¨ Indicar cuántas variables has visualizado en el conjunto de datos y
cuáles son, especificando el tipo de dato asociada a cada una de
ellas.
¨ Clasifica las variables como cualitativas o cuantitativas. Es necesario
que revises todas las variables detenidamente, ya que algunas
variables numéricas podrían considerarse cualitativas.
En caso de que localices una variable cualitativa que inicialmente
sea de tipo numérico deberás remplazar sus valores haciendo uso
de la función replace().
¨ Factorizar todas las variables categóricas, entre las que se encuentran
todas las variables cualitativas.
¨ Crearás un nuevo dataframe llamado “clean_data” sin la columna
llamada: “customerID”
6
TRABAJO FINAL: CIENCIA DE DATOS
Diagramas e histogramas
Haciendo uso del dataframe llamado “clean_data” deberás realizar un diagrama
de frecuencia para cada una de las variables cualitativas del conjunto de datos y
un histograma para cada una de las variables cuantitativas.
Diagramas e histogramas en función del Churn
En este apartado realizarás el mismo ejercicio que en el apartado anterior, pero
coloreando los gráficos anteriores según la variable “Churn”. A continuación, se
mostrará un ejemplo de cómo deberían mostrarse los diagramas de frecuencia y
los histogramas:
Boxplots
Para cada una de las variables cualitativas deberás realizar un boxplot que muestre
la distribución en función del gasto mensual (“MonthlyCharges”). Ejemplo:
7
TRABAJO FINAL: CIENCIA DE DATOS
Gráfico de dispersión
Para cada una de las variables cuantitativas deberás realizar un gráfico de dispersión
que muestre la correlación que hay entre sí. Puedes hacerlo uno a uno o
utilizando un gráfico de correlación conjunto. Ejemplo:
8
TRABAJO FINAL: CIENCIA DE DATOS
EJERCICIO 2 – MODELO DE REGRESIÓN
En primer lugar, será necesario dividir el conjunto de datos clean_data en dos
subconjuntos, uno de entrenamiento que se llamará churn_train1 y otro de pruebas
que se llamará churn_test1, de la siguiente forma:
n El dataframe churn_train1 contendrá las 5000 primeras columnas del
conjunto de datos llamado clean_data
n El dataframe churn_test1 contendrá las filas restantes del dataframe
clean_data, es decir, a partir del registro 5001 hasta el registro final (ambos
inclusive).
Diseño del modelo de regresión
Diseña un modelo de regresión multilineal llamado: lmodel, sobre el conjunto de
entrenamiento churn_train1, teniendo en cuenta la siguiente información:
n Deberás utilizar los datos del conjunto llamado clean_data
n Deberás utilizar como variable objetivo “MonthlyCharges”.
n Deberás utilizar como variables predictoras todas menos “TotalCharges”
y “Churn”.
Tras ello muestra los detalles del modelo con la función summary() y responde
las siguientes preguntas:
n ¿Cuáles son las variables/coeficientes que a un nivel de significancia del
95% podemos concluir que son “no nulos”?
n A partir del valor de los coeficientes, ¿cuál sería la estimación de los diferentes
servicios: teléfono, DSL, Fibra, seguridad, TV, … ?
Por último, deberás realizar una predicción sobre el conjunto: churn_test1 y calcular
el error promedio de las predicciones, utilizando cómo métrica el RMSE (root
mean square error)
9
TRABAJO FINAL: CIENCIA DE DATOS
EJERCICIO 3 – MODELO DE CLASIFICACIÓN
Para la realización de este ejercicio crearás un nuevo conjunto de datos llamado:
clean_data2. Este deberá contener toda la información de clean_data eliminando
la columna “TotalCharges”.
Haciendo uso del conjunto de datos clean_data2 deberás diseñar varios modelos
de clasificación que permitan predecir la cantidad de clientes que pueden abandonar
la compañía. Para ello será necesario dividir el conjunto de datos
clean_data2 en dos subconjuntos, uno de entrenamiento que se llamará
churn_train2 y otro de pruebas que se llamará churn_test2, de la siguiente forma:
n El dataframe churn_train2 contendrá las 5000 primeras columnas del
conjunto de datos llamado clean_data2
n El dataframe churn_test2 contendrá las filas restantes del dataframe
clean_data2, es decir, a partir del registro 5001 hasta el registro final (ambos
inclusive).
Modelo de clasificación 1
Diseña un modelo de clasificación llamado: gmodel1, sobre el conjunto de entrenamiento
churn_train2, teniendo en cuenta la siguiente información:
n Deberás utilizar los datos del conjunto llamado clean_data2
n Deberás utilizar como variable objetivo “Churn”.
n Deberás utilizar todas las variables como predictoras.
Después, deberás realizar la predicción del modelo sobre los datos del conjunto
de testeo churn_test2, para obtener la probabilidad de abandono de los clientes.
A partir de dicha probabilidad tendrás que a asignar a una variable llamada:
churn_pred el valor “Yes” si la predicción es mayor de 0.5 y el valor “No” en caso
contrario.
Tras ello será necesario que calcules la matriz de confusión en función de la siguiente
tabla, también conocida como matriz de confusión:
10
TRABAJO FINAL: CIENCIA DE DATOS
MATRIZ DE CONFUSIÓN
A partir de la matriz de confusión, deberás calcular y mostrar:
n La precisión global de la predicción (accuracy), que se calcula mediante
el uso de la siguiente fórmula:
Precisión = (TP + TN) / (TP + TN + FP + FN)
n El ratio de falsos positivos (FPR) que se calcula mediante el uso de la
siguiente fórmula:
FPR = FP / (FP + TN)
n El ratio de falsos negativos (FNR) que se calcula mediante el uso de la
siguiente fórmula:
FNR = FN / (FN + TP)
n El ratio de verdaderos positivos (TPR) que se calcula mediante el uso de
la siguiente fórmula:
TPR = TP / (TP + FN)
REAL
NO YES
PREDICCIÓN
NO TN FN
YES FP TP
11
TRABAJO FINAL: CIENCIA DE DATOS
Modelo de clasificación 2
En este apartado deberás diseñar un modelo de clasificación llamado: gmodel2,
teniendo en cuenta la siguiente información:
n Deberás utilizar los datos del conjunto llamado clean_data2
n Deberás utilizar como variable objetivo “Churn”.
n Deberás utilizar como variables predictoras únicamente: “Contract”, “Tenure”
e “InternetService”.
Para la realización de este apartado deberás seguir todos los pasos que seguiste
para la realización del “Modelo de clasificación 1”, en caso contrario esta sección
no se dará como válida.
12
TRABAJO FINAL: CIENCIA DE DATOS
EJERCICIO 4 – SIMULACIÓN DE CAMPAÑA
En este ejercicio será necesario evaluar el rendimiento económico de una campaña
de retención de clientes y para ello, será necesario que diseñes un modelo
de clasificación llamado: gmodel3, sobre el conjunto de entrenamiento
churn_train2, teniendo en cuenta la siguiente información:
n Deberás utilizar los datos del conjunto llamado clean_data2
n Deberás utilizar como variable objetivo “Churn”.
n Deberás utilizar todas las variables como predictoras.
Una vez diseñado, será necesario realizar la predicción del modelo sobre los datos
del conjunto de testeo: churn_test2, para obtener la probabilidad de abandono
de los clientes. A partir de dicha probabilidad tendrás que a asignar a una
variable llamada: churn_pred el valor “Yes” si la predicción es mayor de 0.5 y el
valor “No” en caso contrario.
Tras ello será necesario que calcules la matriz de confusión en función de la tabla
planteada en el ejercicio anterior.
Con esta información, podrás calcular el rendimiento de la campaña teniendo en
cuenta la siguiente información:
n A los clientes clasificados por el modelo como “Churners” se les ofrecerá
un teléfono de regalo a cambio de que firmen un contrato de permanencia
de un año. El coste del teléfono se denominará CT.
n Los clientes aceptarán el trato con una probabilidad AR
n El beneficio asociado a la retención de un cliente lo estimamos como el
consumo medio anual de un cliente menos el coste de gestión (uso de
infraestructura, facturación, atención al cliente, …).
El retorno medio estimado por cliente retenido se fijará en 500€ y se
denominará R.
n Se estima que la pérdida de un cliente que abandona la compañía es
igual al retorno R que genera la retención, es decir 500€.
13
TRABAJO FINAL: CIENCIA DE DATOS
El rendimiento se deberá calcular en diferentes umbrales de clasificación:
up = (0, 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9 y 1)
y en función de la probabilidad de Churn estimada por el modelo, se clasificarán
a los clientes en: pred_churn = “Yes” si la probabilidad > up o pred_churn = “No”
en caso contrario.
Conforme aumente el umbral de probabilidad, se seleccionarán menos clientes
para la campaña. Por un lado, esto generará menos coste debido al incentivo que
se ofrece, pero por otro lado se obtendrán menos retenciones.
El objetivo del ejercicio será encontrar el umbral óptimo en el que se obtiene un
mayor rendimiento para la campaña.
Para cada umbral de probabilidad, se deberá calcular a partir de la probabilidad
del modelo la variable churn_pred y obtener la matriz de confusión, de forma que
sea posible estimar el beneficio de la campaña, sabiendo que:
Beneficio = Resultado con campaña – Resultado sin campaña
Resultado con campaña = -FP * AR * I – TP * AR * I – TP * (1 – AR) * R – FN * R
Donde:
n El primer y segundo término hace referencia al gasto de los teléfonos
que regala la compañía a los clientes que aceptan la promoción y que no
hubiesen abandonado la compañía, aunque no se hubiese realizado la
campaña.
n El tercer término representa la perdida de los clientes a los que se les ha
hecho la promoción, no la han aceptado y se han marchado.
n El cuarto representa a los clientes a los que no se les ha realizado la promoción
y han acabado marcándose.
Resultado sin campaña: - (FN + TP) * R
Donde este valor representa la pérdida de ingresos debido al abandono real de
los clientes, en caso de no haber realizado la campaña. Notad que ese término
no depende del modelo ajustado ni de los umbrales de probabilidad.
14
TRABAJO FINAL: CIENCIA DE DATOS
Es importante tener en cuenta que el resultado en ambos casos es un número
negativo, ya que solo se están teniendo en cuenta las pérdidas económicas, ya
sea por gasto de promoción o por la facturación esperada a futuro de un cliente
que abandona la compañía.
Usando esta información, calcula los resultados de la campaña en dos escenarios
de incentivos distintos.
ESCENARIO 1
Para el primer supuesto vamos a contar con la siguiente información:
n Coste del teléfono = 200€ (I)
n Probabilidad de aceptación = 0.4 (AR)
n R = 500€
Con ella, deberás calcular para cada umbral de probabilidad el beneficio de la
campaña utilizando las fórmulas indicadas anteriormente, para finalmente responder:
n ¿Cuál sería el umbral de probabilidad para la selección de clientes óptimo
para la campaña?
n ¿Qué beneficios generaría?
ESCENARIO 2
Para el segundo supuesto vamos a contar con la siguiente información:
n Coste del teléfono = 400€ (I)
n Probabilidad de aceptación = 0.8 (AR)
n R = 500€
Con ella, deberás calcular para cada umbral de probabilidad el beneficio de la
campaña utilizando las fórmulas indicadas anteriormente, para finalmente responder:
n ¿Cuál sería el umbral de probabilidad para la selección de clientes óptimo
para la campaña?
n ¿Qué beneficios generaría?
15
TRABAJO FINAL: CIENCIA DE DATOS
COMPARATIVA
Finalmente, deberás explicar en qué campaña (Escenario 1 o Escenario 2) se obtienen
mejores beneficios, intentando argumentar el por qué.
16
TRABAJO FINAL: CIENCIA DE DATOS
PRESENTACIÓN
Se valorará positivamente la presentación del archivo .Rmd, mediante el uso de
las opciones de formato disponibles para crear un documento atractivo que combine
explicaciones bien estructuradas y bloques de código en R.
Ejemplo en R:
Ejemplo en HTML:
