![Imagen de WhatsApp 2024-06-04 a las 18 26 19_643106cc](https://github.com/MCD-Infrati/etlproject-ca3/assets/137736436/34723dc8-31be-4a65-a78f-8aaf4e705138)
# 1. LOCAL - AmesProperty
Empecemos con lo que se encuentra a nivel Local, el AmesProperty:
Para este archivo se solicita una transformación en donde se tomen los valores nulos de la columna Year Remod/add y se reemplacen por los valores de Year Built.
Esto es mucho más sencillo de lo que parece a simple vista, pues utilizando la transformación "Calculator" incluimos un "New Field" con el nombre deseado, en este caso usamos el mismo Year Remod/Add.
Posteriormente usamos la calculation NVL(A,B) Y utilizamos como field A: Year Remod/Add (el original)  y como field B Year Built. Finalmente indicamos que el tipo de dato es Integer y en Remove ponemos "N". 
Esto nos permite tener la transformación lista para posteriormente juntarla en un solo archivo csv junto con los archivos que se encuentran en la nube.
