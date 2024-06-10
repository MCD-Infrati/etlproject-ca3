# 3. Descripción de las fuentes

Se tienen tres fuentes de datos heterogéneas  como Archivo de datos Ames Property.csv, script sql y datos de conexión MongoDB, las cuales se  extraerán, transformarán y cargarán de los datos en un pipeline través de la herramienta PENTAHO.

## 3.1 Archivo CSV

|Campos|Fuente|Tabla|Descripción|Columa nro.|
|:----|:----|:----|:----|:----|
|PID|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|1|
|Lot Frontage|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|2|
|Lot Area|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|3|
|Street|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|4|
|Alley|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|5|
|Lot Shape|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|6|
|Land Contour|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|7|
|Utilities|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|8|
|Lot Config|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|9|
|Land Slope|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|10|
|Neighborhood|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|11|
|Condition 1|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|12|
|Condition 2|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|13|
|Bldg Type|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|14|
|House Style|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|15|
|Overall Qual|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|16|
|Overall Cond|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|17|
|Year Built|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|18|
|Year Remod/Add|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|19|

# 3.2  BD Relacion (PostgreSQL)

|PID|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|1|
|:----|:----|:----|:----|:----|
|MS SubClass|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|2|
|MS Zoning|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|3|
|Roof Style|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|4|
|Roof Matl|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|5|
|Exterior 1st|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|6|
|Exterior 2nd|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|7|
|Mas Vnr Type|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|8|
|Mas Vnr Area|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|9|
|Exter Qual|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|10|
|Exter Cond|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|11|
|Foundation|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|12|
|Heating|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|13|
|Heating QC|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|14|
|Central Air|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|15|
|Electrical|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|16|
|1st Flr SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|17|
|2nd Flr SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|18|
|Low Qual Fin SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|19|
|Kitchen AbvGr|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|20|
|Kitchen Qual|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|21|
|TotRms AbvGrd|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|22|
|Functional|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|23|
|Fireplaces|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|24|
|Fireplace Qu|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|25|
|Paved Drive|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|26|
|Wood Deck SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|27|
|Open Porch SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|28|
|Enclosed Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|29|
|3Ssn Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|30|
|Screen Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|31|
|Fence|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|32|
|Code|BD_Relacional|MSSubClass|Clase de construcción|1|
|Description|BD_Relacional|MSSubClass|Clase de construcción|2|
|Id|BD_Relacional|MSZoning|Sin descripción|1|
|Code|BD_Relacional|MSZoning|Sin descripción|2|
|Description|BD_Relacional|MSZoning|Sin descripción|3|
|Id|BD_Relacional|TipeQuality|Tipos de calidad|1|
|Code|BD_Relacional|TipeQuality|Tipos de calidad|2|
|Description|BD_Relacional|TipeQuality|Tipos de calidad|3|
|PID|BD_Relacional|SaleProperties|Sin descripción|1|
|Sale date|BD_Relacional|SaleProperties|Sin descripción|2|
|Sale type|BD_Relacional|SaleProperties|Sin descripción|3|
|Sale condition|BD_Relacional|SaleProperties|Sin descripción|4|
|SalePrice|BD_Relacional|SaleProperties|Sin descripción|5|
|PID|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|1|
|Floor|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|2|
|Bedroom|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|3|
|Full Bath|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|4|
|Half Bath|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|5|

# 3.3 BD Mongo 

|PID|MongoDB Atlas|Garage|Sin descripción|1|
|:----|:----|:----|:----|:----|
|Garage Type|MongoDB Atlas|Garage|Sin descripción|2|
|Garage Yr Blt|MongoDB Atlas|Garage|Sin descripción|3|
|Garage Finish|MongoDB Atlas|Garage|Sin descripción|4|
|Garage Cars|MongoDB Atlas|Garage|Sin descripción|5|
|Garage Area|MongoDB Atlas|Garage|Sin descripción|6|
|Garage Qual|MongoDB Atlas|Garage|Sin descripción|7|
|Garage Cond|MongoDB Atlas|Garage|Sin descripción|8|
|PID|MongoDB Atlas|Pool|Sin descripción|1|
|Pool area|MongoDB Atlas|Pool|Sin descripción|2|
|Pool QC|MongoDB Atlas|Pool|Sin descripción|3|
|PID|MongoDB Atlas|bsmt|Sin descripción|1|
|Bsmt Qual|MongoDB Atlas|bsmt|Sin descripción|2|
|Bsmt Cond|MongoDB Atlas|bsmt|Sin descripción|3|
|Bsmt Exposure|MongoDB Atlas|bsmt|Sin descripción|4|
|BsmtFin Type 1|MongoDB Atlas|bsmt|Sin descripción|5|
|BsmtFin SF 1|MongoDB Atlas|bsmt|Sin descripción|6|
|BsmtFin Type 2|MongoDB Atlas|bsmt|Sin descripción|7|
|BsmtFin SF 2|MongoDB Atlas|bsmt|Sin descripción|8|
|Bsmt Unf SF|MongoDB Atlas|bsmt|Sin descripción|9|
|Total Bsmt SF|MongoDB Atlas|bsmt|Sin descripción|10|
|Bsmt Full Bath|MongoDB Atlas|bsmt|Sin descripción|11|
|Bsmt Half Bath|MongoDB Atlas|bsmt|Sin descripción|12|
|PID|MongoDB Atlas|misc|Sin descripción|1|
|Misc feature|MongoDB Atlas|misc|Sin descripción|2|
|Misc Val|MongoDB Atlas|misc|Sin descripción|3|

#3.4  Diccionario del archivo output

|Nro.|Campo|Fuente|Tabla|Descripción|Columa nro. (en la fuente)|Transformaciones|
|:----|:----|:----|:----|:----|:----|:----|
|1|PID|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|1|Se debe validar todas las tablas y ver cuál tiene más registros|
|2|MS SubClass|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|2| |
|3|MS Zoning|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|3| |
|4|Lot Frontage|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|2| |
|5|Lot Area|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|3| |
|6|Street|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|4| |
|7|Alley|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|5| |
|8|Lot Shape|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|6| |
|9|Land Contour|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|7| |
|10|Utilities|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|8| |
|11|Lot Config|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|9| |
|12|Land Slope|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|10| |
|13|Neighborhood|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|11| |
|14|Condition 1|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|12| |
|15|Condition 2|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|13| |
|16|Bldg Type|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|14| |
|17|House Style|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|15| |
|18|Overall Qual|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|16| |
|19|Overall Cond|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|17| |
|20|Year Built|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|18| |
|21|Year Remod/Add|Ames Property.CSV|Ames Property.CSV|Información general de la propiedad|19| |
|22|Roof Style|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|4| |
|23|Roof Matl|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|5| |
|24|Exterior 1st|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|6| |
|25|Exterior 2nd|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|7| |
|26|Mas Vnr Type|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|8| |
|27|Mas Vnr Area|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|9| |
|28|Exter Qual|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|10| |
|29|Exter Cond|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|11| |
|30|Foundation|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|12| |
|31|Bsmt Qual|MongoDB Atlas|bsmt|Sin descripción|2| |
|32|Bsmt Cond|MongoDB Atlas|bsmt|Sin descripción|3| |
|33|Bsmt Exposure|MongoDB Atlas|bsmt|Sin descripción|4| |
|34|BsmtFin Type 1|MongoDB Atlas|bsmt|Sin descripción|5| |
|35|BsmtFin SF 1|MongoDB Atlas|bsmt|Sin descripción|6| |
|36|BsmtFin Type 2|MongoDB Atlas|bsmt|Sin descripción|7| |
|37|BsmtFin SF 2|MongoDB Atlas|bsmt|Sin descripción|8| |
|38|Bsmt Unf SF|MongoDB Atlas|bsmt|Sin descripción|9| |
|39|Total Bsmt SF|MongoDB Atlas|bsmt|Sin descripción|10| |
|40|Heating|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|13| |
|41|Heating QC|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|14| |
|42|Central Air|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|15| |
|43|Electrical|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|16| |
|44|1st Flr SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|17| |
|45|2nd Flr SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|18| |
|46|Low Qual Fin SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|19| |
|47|Gr Liv Area|Campo calculado|Campo calculado| | |Pies cuadrados de superficie habitable sobre el nivel del suelo (suelo). Se calcula a partir de la suma de los campos: 1st Flr SF, 2nd Flr SF y Low Qual Fin SF.|
|48|Bsmt Full Bath|MongoDB Atlas|bsmt|Sin descripción|11| |
|49|Bsmt Half Bath|MongoDB Atlas|bsmt|Sin descripción|12| |
|50|Full Bath|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|4|Se deben calcular teniendo en cuenta que una propiedad puede tener varios pisos. En la tabla FloorDetail se encuentran los datos de cantidad de habitaciones, y baños, por piso para cada propiedad. La transformación consiste en calcular el total de baños FullBath, HalfBath, Bedroom.|
|51|Half Bath|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|5|Se deben calcular teniendo en cuenta que una propiedad puede tener varios pisos. En la tabla FloorDetail se encuentran los datos de cantidad de habitaciones, y baños, por piso para cada propiedad. La transformación consiste en calcular el total de baños FullBath, HalfBath, Bedroom.|
|52|Bedroom AbvGr|BD_Relacional|FloorDetail|Para cada propiedad por piso, se encuentra la cantidad de habitaciones y baños.|3|Se deben calcular teniendo en cuenta que una propiedad puede tener varios pisos. En la tabla FloorDetail se encuentran los datos de cantidad de habitaciones, y baños, por piso para cada propiedad. La transformación consiste en calcular el total de baños FullBath, HalfBath, Bedroom.|
|53|Kitchen AbvGr|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|20| |
|54|Kitchen Qual|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|21| |
|55|TotRms AbvGrd|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|22| |
|56|Functional|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|23| |
|57|Fireplaces|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|24| |
|58|Fireplace Qu|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|25| |
|59|Garage Type|MongoDB Atlas|Garage|Sin descripción|2| |
|60|Garage Yr Blt|MongoDB Atlas|Garage|Sin descripción|3| |
|61|Garage Finish|MongoDB Atlas|Garage|Sin descripción|4| |
|62|Garage Cars|MongoDB Atlas|Garage|Sin descripción|5| |
|63|Garage Area|MongoDB Atlas|Garage|Sin descripción|6| |
|64|Garage Qual|MongoDB Atlas|Garage|Sin descripción|7| |
|65|Garage Cond|MongoDB Atlas|Garage|Sin descripción|8| |
|66|Paved Drive|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|26| |
|67|Wood Deck SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|27| |
|68|Open Porch SF|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|28| |
|69|Enclosed Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|29| |
|70|3Ssn Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|30| |
|71|Screen Porch|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|31| |
|72|Pool Area|MongoDB Atlas|Pool|Sin descripción|2| |
|73|Pool QC|MongoDB Atlas|Pool|Sin descripción|3| |
|74|Fence|BD_Relacional|Amesdbtemp|Detalles relacionados con la construcción|32| |
|75|Misc Feature|MongoDB Atlas|misc|Sin descripción|2| |
|76|Misc Val|MongoDB Atlas|misc|Sin descripción|3| |
|77|Mo Sold|Campo calculado| | | |En la tabla saleProperty se encuentra la fecha de venta y se requiere que en la salida esté solo mes (Mo Sold) y año de venta (Yr Sold).|
|78|Yr Sold|Campo calculado| | | |En la tabla saleProperty se encuentra la fecha de venta y se requiere que en la salida esté solo mes (Mo Sold) y año de venta (Yr Sold).|
|79|Sale Type|BD_Relacional|SaleProperties|Sin descripción|3| |
|80|Sale Condition|BD_Relacional|SaleProperties|Sin descripción|4| |
|81|SalePrice|BD_Relacional|SaleProperties|Sin descripción|5| |


