# 6. Ajuste en las fuentes de datos 

Identificar los campos requeridos como resultado es clave para optimizar los recursos. En este sentido, buscamos la fuente para cada campo esperado, reconociendo que no todos los campos en las fuentes debían ser mapeados. 

Dado que contamos con diferentes fuentes de información, algunas ubicadas en la nube y otras locales, es esencial establecer una estrategia de integración eficiente. 

Esto incluye la verificación de la disponibilidad y calidad de los datos en cada fuente, así como la implementación de mecanismos que aseguren la consistencia y sincronización de la información entre los sistemas locales y en la nube. 

De esta manera, se garantiza que los datos relevantes sean accesibles y precisos, permitiendo una toma de decisiones informada y efectiva.

Es importante identificar el tipo de informacion que proveen y total de regsitro en cada fuente de informacion para el momento en que se haga el merge de los campos utilizar de forma correcta la cardinalidad.

## 6.1 Archivo CSV
  En el caso del archivo, se analizaron los campos que se esperaban y todos eran necesarios, por lo que en el paso correspondiente de Pentaho se tomaron todos. Se cuenta con informacón de 2930 apartamentos.

## 6.2 Mongo DB 
  En Mongo DB Atlas se proporcionaron la base de datos "test" que contenía 4 tablas, los datos en estas tablas corresponden a:

    *- Basement:* Analizando los datos, el universo de datos es de 2851 registros, lo que nos hace ver que no todos los apartamentos tienen un sótano. 
    *- garage:* Se tiene informacion de 2773 parqueaderos para los apartamentos, lo que nos hace ver que no todos los apartamentos tienen un garage. 
    *- misc:* 106 apartamentos tienen miscelaneos.
    *- pool:* solo 13 apartamentos tienen piscina.


## 6.3 BD Relacional en Elephant

### Tablas

    *- amesdbtemp:* Decripción general de las propiedades, se cuentan con la informacion de 2930 propiedades.
    *- floordetail:* Informacion de habitaciones y baños para cada piso de la propiedad. Se tienen 4182 registros, que al analizar muestran la informacion de cada piso de la propiedad. Al sumarizar la información en la vista vfloor_sum por apartamento, se obtienen la información para 2930 propiedades.
    *- mssubclass:* Subclase de vivienda, en total hay 16 tipos identificados.
    *- mszoning:* Zonas, la clasificación tiene un total de 8 zonas.
    *- salesproperty: Informacion con el precio de venta de las propiedades, con un total de 2930 entradas correspondiente a cada propiedad.
    *- typequality:* Se asigna una descrición a una escala de calidad, 5 tipos identificados. 

### Vistas
    *- vfloor_sum:* Vista de la tabla floordetail, sumarizado el numero de habitaciones y baños por propiedad.

    Codigo SQL de la vista:
        SELECT floordetail.pid,
            sum(floordetail.bedrooms) AS bedrooms,
            sum(floordetail."Full Bath") AS "Full Bath",
            sum(floordetail."Half Bath") AS "Half Bath"
        FROM floordetail
        GROUP BY floordetail.pid;

    *- vmaes:* Vista que integra la informacion desde la tabla amesdbtemp, uniendo con la vista vfloor_sum con las tablas mssubclass, mszoning, salesproperty y typequality. EL join que se crea en cada una de estas uniones es del tipo LEFT JOIN a sabiendas de que las tablas a la derecha no siempre tienen registros, en los casos que no hay una correspondencia se llena el valor con Null. El campo utilizado para estos join es el PID, que corresponde a la clave de la propiedad.

    La vista creada fue creado con el siguiente SQL:
        SELECT amesdbtemp.pid,
            mssubclass.description AS "MS SubClass",
            mszoning.code AS "MS Zoning",
            amesdbtemp."Roof Style",
            amesdbtemp."Roof Matl",
            amesdbtemp."Exterior 1st",
            amesdbtemp."Exterior 2nd",
            amesdbtemp."Mas Vnr Type",
            amesdbtemp."Mas Vnr Area",
            equal.code AS "Exter Qual",
            econd.code AS "Exter Cond",
            amesdbtemp.foundation,
            amesdbtemp.heating,
            heat.code AS "Heating QC",
            amesdbtemp."Central Air",
            amesdbtemp.electrical,
            amesdbtemp."1st Flr SF",
            amesdbtemp."2nd Flr SF",
            amesdbtemp."Low Qual Fin SF",
            amesdbtemp."Kitchen AbvGr",
            kitchen.code AS "Kitchen Qual",
            amesdbtemp."TotRms AbvGrd",
            amesdbtemp.functional,
            amesdbtemp.fireplaces,
            amesdbtemp."Fireplace Qu",
            amesdbtemp."Paved Drive",
            amesdbtemp."Wood Deck SF",
            amesdbtemp."Open Porch SF",
            amesdbtemp."Enclosed Porch",
            amesdbtemp."3Ssn Porch",
            amesdbtemp."Screen Porch",
            amesdbtemp.fence,
            sum(amesdbtemp."1st Flr SF" + amesdbtemp."2nd Flr SF" + amesdbtemp."Low Qual Fin SF")::integer AS "Gr Liv Area",
            vfloor_sum.bedrooms::integer AS bedrooms,
            vfloor_sum."Full Bath"::integer AS "Full Bath",
            vfloor_sum."Half Bath"::integer AS "Half Bath",
            date_part('month'::text, saleproperty."Sale Date")::integer AS "Mo Sold",
            date_part('year'::text, saleproperty."Sale Date")::integer AS "Yr Sold",
            saleproperty."Sale Type",
            saleproperty."Sale Condition",
            saleproperty.saleprice
        FROM amesdbtemp
            LEFT JOIN vfloor_sum ON vfloor_sum.pid = amesdbtemp.pid
            LEFT JOIN saleproperty ON saleproperty.pid = amesdbtemp.pid
            LEFT JOIN mssubclass ON mssubclass.code = amesdbtemp."MS SubClass"
            LEFT JOIN mszoning ON mszoning.id = amesdbtemp."MS Zoning"
            LEFT JOIN typequality heat ON heat.id = amesdbtemp."Heating QC"
            LEFT JOIN typequality kitchen ON kitchen.id = amesdbtemp."Kitchen Qual"
            LEFT JOIN typequality equal ON equal.id = amesdbtemp."Exter Qual"
            LEFT JOIN typequality econd ON econd.id = amesdbtemp."Exter Cond"
        GROUP BY amesdbtemp.pid, mssubclass.description, heat.code, kitchen.code, equal.code, econd.code, mszoning.code, vfloor_sum.bedrooms, vfloor_sum."Full Bath", vfloor_sum."Half Bath", saleproperty."Sale Date", saleproperty."Sale Type", saleproperty."Sale Condition", saleproperty.saleprice
        ORDER BY amesdbtemp.pid;