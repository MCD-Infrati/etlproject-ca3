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

## 8.4.1 Campos del archivo
Los campos que conforman el archivo de salida se describen a continuación:

|Posición|Campo|Fuente|Tabla|Descripción| 
|:----|:----|:----|:----|:----| 
|1|PID|Ames Property.CSV|Ames Property.CSV|Id de la Propiedad| 
|2|MS SubClass|BD_Relacional|Amesdbtemp|Clase de construcción| 
|3|MS Zoning|BD_Relacional|Amesdbtemp|Clasificación general de zonificación| 
|4|Lot Frontage|Ames Property.CSV|Ames Property.CSV|Pies lineales de calle conectados a la propiedad| 
|5|Lot Area|Ames Property.CSV|Ames Property.CSV|Tamaño del lote en pies cuadrados| 
|6|Street|Ames Property.CSV|Ames Property.CSV|Tipo de acceso vial| 
|7|Alley|Ames Property.CSV|Ames Property.CSV|Tipo de acceso al callejón| 
|8|Lot Shape|Ames Property.CSV|Ames Property.CSV|Forma general de la propiedad| 
|9|Land Contour|Ames Property.CSV|Ames Property.CSV|Planitud de la propiedad| 
|10|Utilities|Ames Property.CSV|Ames Property.CSV|Tipo de utilidades disponibles| 
|11|Lot Config|Ames Property.CSV|Ames Property.CSV|configuración del lote| 
|12|Land Slope|Ames Property.CSV|Ames Property.CSV|Pendiente de la propiedad| 
|13|Neighborhood|Ames Property.CSV|Ames Property.CSV|ubicaciones físicas dentro de los límites de la ciudad de Ames| 
|14|Condition 1|Ames Property.CSV|Ames Property.CSV|Proximidad a una carretera principal o vía férrea| 
|15|Condition 2|Ames Property.CSV|Ames Property.CSV|Proximidad a una carretera principal o vía férrea (si hay una segunda)| 
|16|Bldg Type|Ames Property.CSV|Ames Property.CSV|Tipo de vivienda| 
|17|House Style|Ames Property.CSV|Ames Property.CSV|Estilo de vivienda| 
|18|Overall Qual|Ames Property.CSV|Ames Property.CSV|calidad general del material y del acabado.| 
|19|Overall Cond|Ames Property.CSV|Ames Property.CSV|Calificación de condición general| 
|20|Year Built|Ames Property.CSV|Ames Property.CSV|fecha de construcción original| 
|21|Year Remod/Add|Ames Property.CSV|Ames Property.CSV|fecha de remodelación| 
|22|Roof Style|BD_Relacional|Amesdbtemp|Tipo de techo| 
|23|Roof Matl|BD_Relacional|Amesdbtemp|Material del tejado| 
|24|Exterior 1st|BD_Relacional|Amesdbtemp|Revestimiento exterior de la casa.| 
|25|Exterior 2nd|BD_Relacional|Amesdbtemp|Revestimiento exterior de la casa (si hay más de un material)| 
|26|Mas Vnr Type|BD_Relacional|Amesdbtemp|Tipo de revestimiento de mampostería| 
|27|Mas Vnr Area|BD_Relacional|Amesdbtemp|Área de revestimiento de mampostería en pies cuadrados| 
|28|Exter Qual|BD_Relacional|Amesdbtemp|Calidad del material exterior| 
|29|Exter Cond|BD_Relacional|Amesdbtemp|Estado actual del material en el exterior.| 
|30|Foundation|BD_Relacional|Amesdbtemp|Tipo de cimentación| 
|31|Bsmt Qual|MongoDB Atlas|bsmt|Altura del sótano| 
|32|Bsmt Cond|MongoDB Atlas|bsmt|Estado general del sótano.| 
|33|Bsmt Exposure|MongoDB Atlas|bsmt|Paredes de sótano a nivel de jardín o de salida| 
|34|BsmtFin Type 1|MongoDB Atlas|bsmt|Calidad del área terminada del sótano| 
|35|BsmtFin SF 1|MongoDB Atlas|bsmt|Pies cuadrados acabados tipo 1| 
|36|BsmtFin Type 2|MongoDB Atlas|bsmt|Calidad de la segunda área terminada (si está presente)| 
|37|BsmtFin SF 2|MongoDB Atlas|bsmt|Pies cuadrados acabados tipo 2| 
|38|Bsmt Unf SF|MongoDB Atlas|bsmt|Metros cuadrados de sótano sin terminar| 
|39|Total Bsmt SF|MongoDB Atlas|bsmt|Pies cuadrados totales de área del sótano| 
|40|Heating|BD_Relacional|Amesdbtemp|Tipo de calefacción| 
|41|Heating QC|BD_Relacional|Amesdbtemp|Calidad y estado de la calefacción| 
|42|Central Air|BD_Relacional|Amesdbtemp|aire acondicionado centralizado| 
|43|Electrical|BD_Relacional|Amesdbtemp|Sistema eléctrico| 
|44|1st Flr SF|BD_Relacional|Amesdbtemp|Pies cuadrados del primer piso| 
|45|2nd Flr SF|BD_Relacional|Amesdbtemp|Pies cuadrados del segundo piso| 
|46|Low Qual Fin SF|BD_Relacional|Amesdbtemp|Pies cuadrados con acabado de baja calidad (todos los pisos)| 
|47|Gr Liv Area|Campo calculado|Campo calculado|superficie habitable sobre el nivel del suelo (pies cuadrados)| 
|48|Bsmt Full Bath|MongoDB Atlas|bsmt|Baños completos en sótano| 
|49|Bsmt Half Bath|MongoDB Atlas|bsmt|Medios baños del sótano| 
|50|Full Bath|BD_Relacional|FloorDetail|Baños completos sobre el nivel del suelo.| 
|51|Half Bath|BD_Relacional|FloorDetail|Medios baños sobre el nivel del suelo.| 
|52|Bedroom AbvGr|BD_Relacional|FloorDetail|Promedio de Baños| 
|53|Kitchen AbvGr|BD_Relacional|Amesdbtemp|Promedio de Cocinas| 
|54|Kitchen Qual|BD_Relacional|Amesdbtemp|Calidad de cocina| 
|55|TotRms AbvGrd|BD_Relacional|Amesdbtemp|Total de habitaciones sobre rasante (no incluye baños)| 
|56|Functional|BD_Relacional|Amesdbtemp|Calificación de funcionalidad del hogar| 
|57|Fireplaces|BD_Relacional|Amesdbtemp|Número de chimeneas| 
|58|Fireplace Qu|BD_Relacional|Amesdbtemp|Calidad de chimenea| 
|59|Garage Type|MongoDB Atlas|Garage|Ubicación del garaje| 
|60|Garage Yr Blt|MongoDB Atlas|Garage|Año de construcción del garaje.| 
|61|Garage Finish|MongoDB Atlas|Garage|Acabado interior del garaje.| 
|62|Garage Cars|MongoDB Atlas|Garage|Tamaño del garaje en capacidad de coches.| 
|63|Garage Area|MongoDB Atlas|Garage|tamaño del garaje en pies cuadrados| 
|64|Garage Qual|MongoDB Atlas|Garage|Calidad del garaje| 
|65|Garage Cond|MongoDB Atlas|Garage|Estado del garaje| 
|66|Paved Drive|BD_Relacional|Amesdbtemp|camino pavimentado| 
|67|Wood Deck SF|BD_Relacional|Amesdbtemp|Área de cubierta de madera en pies cuadrados| 
|68|Open Porch SF|BD_Relacional|Amesdbtemp|Área de porche abierto en pies cuadrados| 
|69|Enclosed Porch|BD_Relacional|Amesdbtemp|área del porche cerrado en pies cuadrados| 
|70|3Ssn Porch|BD_Relacional|Amesdbtemp|Área de porche de tres estaciones en pies cuadrados| 
|71|Screen Porch|BD_Relacional|Amesdbtemp|área del porche cubierto en pies cuadrados| 
|72|Pool Area|MongoDB Atlas|Pool|Área de la piscina en pies cuadrados| 
|73|Pool QC|MongoDB Atlas|Pool|Calidad de la piscina| 
|74|Fence|BD_Relacional|Amesdbtemp|Calidad de la valla| 
|75|Misc Feature|MongoDB Atlas|misc|característica miscelánea no cubierta en otras categorías| 
|76|Misc Val|MongoDB Atlas|misc|$Valor de la característica miscelánea| 
|77|Mo Sold|Campo calculado| |Mes Vendido| 
|78|Yr Sold|Campo calculado| |Año vendido| 
|79|Sale Type|BD_Relacional|SaleProperties|Tipo de venta| 
|80|Sale Condition|BD_Relacional|SaleProperties|Condición de venta| 
|81|SalePrice|BD_Relacional|SaleProperties|Precio de Venta| 


## 8.4.2 Ejemplo de archivo

En la carpeta Output se encuentra el archivo de ejemplo:

    Ames_20240614013427.csv

Como se describió al inicio del capitulo, este archivo fue generado el 14/06/2024 a las 01:34:27AM, conteniendo los campos descritos en el punto anterior.