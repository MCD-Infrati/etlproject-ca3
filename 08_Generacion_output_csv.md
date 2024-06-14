## 8. Generación del Output

Una vez que se fusionan todas las fuentes de información se procede a preparar el archivo de salida.

## 8.1 Remover campos no requeridos
Para esto el primer paso que se agrega al proceso es el de remover los campos que no se requieren en el paso posterior, como ya de entrada solo trajimos los campos necesarios, solo los campos PID que se agregaron en el Join son los que se deben remover. Se realizó utilizando el componente Select Values, pero en lugar de seleccionar los que se requieren, excluimos los que no debian considerarse.

## 8.2 Reemplazar los nulos
Una instruccion que tenemos es el reemplazo de los campos nulos, para no tener varios pasos durante el proceso, acá lo dejamos en un único paso para todo el flujo ya que la regla que tenemos aplica de manera general para todos, con el "If field value is null", se indico que si el campo es numero o entero reemplazara el nulo por 0 y en el caso de string se remplaza por NA.

## 8.3 Pasos adicionales sugeridos en el requerimiento
Se presentaron la fuente de información para 3 diccionarios que se pueden utilizar para reemplazar valores en el archivo de salida, esto nos permite cambiar valores clave por una descripción que sea mas representativa para un usuario final.

La recomendación cuando se tienen este tipo de fuente de información es que se haga através de tablas que los valores se pueden mantener a medida que se agreguen nuevos registros o se tenga que hacer alguna modificación, en la vista vames se utilizó este metodo con las tablas mssubclass, mszoning y typequiality que se referenció mas de una vez. En los casos que los valores a sustituir no cambian en el tiempo el metodo de hacerlo con valores HardCode sería la solución recomendada.

Para nuestro caso utilizamos un objeto del tipo Value Mapper para indicar el valor del campo Origen y el Valor destino que esperamos sustituir, asi se cargaron los diccionarios de dato para Lot SHape, Condition 1 y Neighborhood.

## 8.4 Generacion de archivo CSV

En este punto, ya las fuentes de información fueron leídas, los campos nulos reemplazados, los mapeos de diccionarios ya realizados.

Para generar el archivo se utilizo el componente Text file Output, al que se le indicó los siguientes parámetros:
- Nombre del archivo, se le indico un directorio y un prefijo para el nombre del archivo
- Extension, se seleccionó CSV
- Especificar fecha y hora en el nombre
- formato de fecha y hora en el nombre

Por otra parte, en el tab fields, se organizaron todos los campos en la secuencia que fue solicitada en la especificación inicial y se ajustaron la longitud de los campos.

Los campos que conforman el archivo de salida se describen a continuación:




