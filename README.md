# twitter-sentiment-analysis

Está formado por 10 bloques de código.

Ejercicio 1

Calcular para cada tweet un valor denominado “sentimiento del tweet”, que se obtiene como la suma de los “sentimientos” de los términos que aparecen en el tweet.


[1] - Primero, se importan las bibliotecas necesarias para el análisis y la visualización.

 ![](Images/Picture%201.png)


[2] - Aquí se procesan los datos como objeto JSON para cada tweet. En el siguiente bloque de código, leemos estos tweets del archivo salida_tweets.txt donde están almacenados. El archivo .ipynb está ubicado en la misma carpeta donde se almacenan los archivos salida_tweets.txt y Sentimientos.txt, por lo que tweets_data_path será el nombre del propio archivo para no tener en cuenta ninguna ruta relativa al intentar cargar los datos.

 
 ![](Images/Picture%202.png)

[3] - Se crea la función “clean” para eliminar tr, números, urls, menciones, símbolos...etc. y todo lo que entorpece identificar palabras en cada tweet y no aportan nada.
 
 ![](Images/Picture%203.png)
[4] - Se  crea la función “tokenize” para separar el texto de cada tweet en palabras y quitar stopwords.

  ![](Images/Picture%204.png)

[5] - Se implementan las funciones “clean” y “tokenize” para asignar algunos de los parámetros de estos objetos JSON a la columna de ‘text’ de un marco de datos de Pandas donde almacenaremos los tweets de ahora en adelante. 


También se seleccionan sólo los tweets que están en inglés ya que en el archivo “Sentimientos.txt” solo tengo palabras en inglés.
 
 ![](Images/Picture%205.png)

  
[6] - Para utilizar los datos en el archivo “Sentimientos.txt”, a la hora de buscar palabras coincidentes en cada tweet y asignarle su correspondiente valor, se crear un diccionario. Se tiene en cuenta que este archivo está delimitado por tabuladores, lo que significa que el término y la puntuación están separados por un carácter de tabulación. Se utiliza "\ t" para identificar el caracter de tabulación.
 ![](Images/Picture%206.png)

[7] - Para marcar si la palabra está en el diccionario. Si están devuelve un 1, si no un 0.
 ![](Images/Picture%207.png)
 
In [8] (salida del Ejercicio 1) - Este bloque de código es el que irá fila por fila, palabras por palabra para la columna ‘text’ del dataframe anteriormente creado (“tweets”) buscando las palabras con valor 1 y acumulando el valor de las palabras que encuentre en el tweet que coincidan con las del diccionario. El resto de palabras no coincidentes tendrán valor 0. Los resultados se guardan bajo la cabecera de ‘ratings’. Se añade esta columna al dataframe “tweets” para visualizar el valor acumulado de cada tweet.

 ![](Images/Picture%208.png)


Ejercicio 2

Dado un archivo que contiene en cada línea una palabra o conjunto de palabras seguido de un valor numérico denominado “sentimiento” y un conjunto de tweets, se pide calcular el sentimiento de aquellas palabras o conjunto de palabras que no tienen un valor asociado en el archivo de “sentimientos”.

[9] - (salida del Ejercicio 2) - Este bloque de código encuentra las palabras que no estén en el diccionario y les asigna a cada una de estas palabras el valor total del tweet anteriormente calculado. No les asigna ningún valor a las palabras que si se encuentran en el diccionario.
 
 ![](Images/Picture%209.png)


La salida por pantalla de cada tweet va tener la siguiente estructura:

-	Numeración del tweet
-	Valor de las palabras encontradas en el diccionario. En este ejemplo “best”, “good” y “happy” que tiene el valor cada una de 3
-	Palabra no encontrada en el diccionario y el valor que le asignamos. En este caso 9 (3+3+3)
-	Palabra sí encontrada en el diccionario a la que no le asignamos ningún valor

![](Images/Picture%2010.png)
 
[10] - Se añade esta columna al dataframe “tweets” para visualizar el valor acumulado de esta segunda manera de valorar los tweets.
 
 ![](Images/Picture%2011.png)
