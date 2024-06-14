# 3. Descripción de las fuentes

Se tienen tres fuentes de datos heterogéneas  como Archivo de datos Ames Property.csv, script sql y datos de conexión MongoDB, las cuales se  extraerán, transformarán y cargarán de los datos en un pipeline través de la herramienta PENTAHO.

## 3.1 Archivo CSV

|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Lot Frontage|Pies lineales de calle conectados a la propiedad| 
|3|Lot Area|Tamaño del lote en pies cuadrados| 
|4|Street|Tipo de acceso vial| 
|5|Alley|Tipo de acceso al callejón| 
|6|Lot Shape|Forma general de la propiedad| 
|7|Land Contour|Planitud de la propiedad| 
|8|Utilities|Tipo de utilidades disponibles| 
|9|Lot Config|configuración del lote| 
|10|Land Slope|Pendiente de la propiedad| 
|11|Neighborhood|ubicaciones físicas dentro de los límites de la ciudad de Ames| 
|12|Condition 1|Proximidad a una carretera principal o vía férrea| 
|13|Condition 2|Proximidad a una carretera principal o vía férrea (si hay una segunda)| 
|14|Bldg Type|Tipo de vivienda| 
|15|House Style|Estilo de vivienda| 
|16|Overall Qual|calidad general del material y del acabado.| 
|17|Overall Cond|Calificación de condición general| 
|18|Year Built|fecha de construcción original| 
|19|Year Remod/Add|fecha de remodelación| 

 # 3.2 BD Mongo 

 ## 3.2.1 Colección Garage

|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Garage Type|Ubicación del garaje| 
|3|Garage Yr Blt|Año de construcción del garaje.| 
|4|Garage Finish|Acabado interior del garaje.| 
|5|Garage Cars|Tamaño del garaje en capacidad de coches.| 
|6|Garage Area|tamaño del garaje en pies cuadrados| 
|7|Garage Qual|Calidad del garaje| 
|8|Garage Cond|Estado del garaje| 



 ## 3.2.2 Colección Pool

|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Pool area|Área de la piscina en pies cuadrados| 
|3|Pool QC|Calidad de la piscina| 


 ## 3.2.3 Colección bsmt

|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Bsmt Qual|Altura del sótano| 
|3|Bsmt Cond|Estado general del sótano.| 
|4|Bsmt Exposure|Paredes de sótano a nivel de jardín o de salida| 
|5|BsmtFin Type 1|Calidad del área terminada del sótano| 
|6|BsmtFin SF 1|Pies cuadrados acabados tipo 1| 
|7|BsmtFin Type 2|Calidad de la segunda área terminada (si está presente)| 
|8|BsmtFin SF 2|Pies cuadrados acabados tipo 2| 
|9|Bsmt Unf SF|Promedio de cocina| 
|10|Total Bsmt SF|Pies cuadrados totales de área del sótano| 
|11|Bsmt Full Bath|Baños completos en sótano| 
|12|Bsmt Half Bath|Medios baños del sótano| 


 ## 3.2.3 Colección misc

|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Misc feature|característica miscelánea no cubierta en otras categorías| 
|3|Misc Val|$Valor de la característica miscelánea| 

# 3.3  BD Relacion (PostgreSQL)

## 3.3.1 Coleccion Amesdbtemp
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|MS SubClass|Clase de construcción| 
|3|MS Zoning|Clasificación general de zonificación| 
|4|Roof Style|Tipo de techo| 
|5|Roof Matl|Material del tejado| 
|6|Exterior 1st|Revestimiento exterior de la casa.| 
|7|Exterior 2nd|Revestimiento exterior de la casa (si hay más de un material)| 
|8|Mas Vnr Type|Tipo de revestimiento de mampostería| 
|9|Mas Vnr Area|Área de revestimiento de mampostería en pies cuadrados| 
|10|Exter Qual|Calidad del material exterior| 
|11|Exter Cond|Estado actual del material en el exterior.| 
|12|Foundation|Tipo de cimentación| 
|13|Heating|Tipo de calefacción| 
|14|Heating QC|Calidad y estado de la calefacción| 
|15|Central Air|aire acondicionado centralizado| 
|16|Electrical|Sistema eléctrico| 
|17|1st Flr SF|Pies cuadrados del primer piso| 
|18|2nd Flr SF|Pies cuadrados del segundo piso| 
|19|Low Qual Fin SF|Pies cuadrados con acabado de baja calidad (todos los pisos)| 
|20|Kitchen AbvGr|Promedio de cocina| 
|21|Kitchen Qual|Calidad de cocina| 
|22|TotRms AbvGrd|Total de habitaciones sobre rasante (no incluye baños)| 
|23|Functional|Calificación de funcionalidad del hogar| 
|24|Fireplaces|Número de chimeneas| 
|25|Fireplace Qu|Calidad de chimenea| 
|26|Paved Drive|Camino pavimentado| 
|27|Wood Deck SF|Área de cubierta de madera en pies cuadrados| 
|28|Open Porch SF|Área de porche abierto en pies cuadrados| 
|29|Enclosed Porch|Área del porche cerrado en pies cuadrados| 
|30|3Ssn Porch|Área de porche de tres estaciones en pies cuadrados| 
|31|Screen Porch|Área del porche cubierto en pies cuadrados| 
|32|Fence|Calidad de la valla| 

## 3.3.2 Colección MSSubClass
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
 |1|Code|Código de la Subclase| 
 |2|Description|Descripción de la Subclase| 
 

## 3.3.3 Colección MSZoning
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
 |1|Code|Código de zonificación| 
 |2|Description|Descripción de la zonificación| 


## 3.3.4 Colección MSZoning
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
 |1|Code|Código de zonificación| 
 |2|Description|Descripción de la zonificación| 


## 3.3.5 Colección TipeQuality
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|Id|ID  de Tipo de Calidad| 
|2|Code|Código Tipo de Calidad| 
|3|Description|Descripción deTipo de Calidad| 
 

## 3.3.6 Colección SaleProperties
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Sale date|Fecha de Venta| 
|3|Sale type|Tipo de venta| 
|4|Sale condition|Condición de venta| 

 ## 3.3.7 Colección FloorDetail
 
|Columa nro.|Campos|Descripción| 
|:----|:----|:----| 
|1|PID|Id de la Propiedad| 
|2|Floor|Piso| 
|3|Bedroom|Número de dormitorios por encima del nivel del sótano| 
|4|Full Bath|Baños completos sobre el nivel del suelo.| 
|5|Half Bath|Medios baños sobre el nivel del suelo.| 
