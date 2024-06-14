## 7. Merge de las fuentes ##

![Imagen de WhatsApp 2024-06-04 a las 18 26 19_643106cc](https://github.com/MCD-Infrati/etlproject-ca3/assets/137736436/34723dc8-31be-4a65-a78f-8aaf4e705138)


De forma general, cada fuente de informacion que se carga, se verifican los campos si son requeridos para que se lean y se organizan en la lectura en la misma secuencia que esta fuente de informacion entrega al archivo final. Si bien, tecnicamente no aporta en temas de performance el orden, si al momento de hacer validaciones ayuda mucho que los campos esten ordenados.

## 7.1 LOCAL - AmesProperty

Empecemos con lo que se encuentra a nivel Local, el AmesProperty:

Para este archivo se solicita una transformación en donde se tomen los valores nulos de la columna Year Remod/add y se reemplacen por los valores de Year Built.
Esto es mucho más sencillo de lo que parece a simple vista, pues utilizando la transformación "Calculator" incluimos un "New Field" con el nombre deseado, en este caso usamos el mismo Year Remod/Add.

Posteriormente usamos la calculation NVL(A,B) Y utilizamos como field A: Year Remod/Add (el original)  y como field B Year Built. Finalmente indicamos que el tipo de dato es Integer y en Remove ponemos "N". 

En el siguiente paso se realiza un Sort para tener organizado por PID esta fuente de información.

Esto nos permite tener la transformación lista para posteriormente juntarla en un solo archivo csv junto con los archivos que se encuentran en la nube.


## 7.2 Nube - MongoDB 

En el caso de esta fuente de información no fue posible construir vitas en MongoDB, esto por temas de performance, de claridad en el modelo y para distribuir la carga de trabajo hubiera sido ideal, esto derivó que se manejen 4 conecciones a MongoDB. 

## 7.2.1 Colección bsmt 

Desde Mongo DB se lee utilizando un componente de MongoDB Input y el url provisto, el esquema de base de datos test, se selecciona la coleccion bsmt, que contiene los datos de sótanos, en un paso posterior se ordena por PID para dejar preparada para el Join.

Posteriormente se realiza un LEFT JOIN utilizando el componente Merge Join, dejando a la izquierda AmesProperty y a la derecha bsmt, estas fuentes de información se unen utilizando el campo PID de cada uno.


## 7.2.2 Colección garage

Similar a los pasos descritos en 7.2.1, para la coleccion garage se siguen los mismos pasos, conectando a la misma base de datos, pero a la coleccion de parqueaderos.

Se ordena descendientemente por PID en un paso siguiente.

Ahora, utlizando un LEFT JOIN con el resultado del paso anterior, se une con esta nueva colección para ir completando los campos requeridos.

## 7.2.3 Colección pool

Similar a los pasos descritos en 7.2.1, para la coleccion pool se siguen los mismos pasos, conectando a la misma base de datos, pero a la coleccion de piscinas.

Se ordena descendientemente por PID en un paso siguiente.

Ahora, utlizando un LEFT JOIN con el resultado del paso anterior, se une con esta nueva colección para ir completando los campos requeridos.

## 7.2.3 Colección misc

Similar a los pasos descritos en 7.2.1, para la coleccion misc se siguen los mismos pasos, conectando a la misma base de datos, pero a la coleccion de miscelaneos.

Se ordena descendientemente por PID en un paso siguiente.

Ahora, utlizando un LEFT JOIN con el resultado del paso anterior, se une con esta nueva colección para ir completando los campos requeridos.


## 7.3 Nube - PostgreSQL

Utilizando la vista vames, que se describio en el punto 6.3, se procede a unir la información de esta base de datos, con la que ha venido construyendo en los pasos anteriores, para esto se utiliza un Table Input y en el Select se agrega que los datos los regrese ordenados, por lo que no es necesario realizar un paso de sort.

Ahora, utlizando un LEFT JOIN con el resultado del paso anterior, se une con esta nueva colección para finalizar la lectura de los campos requeridos.

## 7.4 Flujo en Pentaho del proceso

EL siguiente flujo describe los pasos creados en Pentaho para la generación del archivo:

[![Flujo Pentaho de Creacion de Archivo](https://github.com/MCD-Infrati/etlproject-ca3/blob/main/imagenes/CA3%Ames%Transformation.jpg "Flujo Pentaho de Creacion de Archivo")](https://github.com/MCD-Infrati/etlproject-ca3/blob/main/imagenes/CA3%Ames%Transformation.jpg "Flujo Pentaho de Creacion de Archivo")