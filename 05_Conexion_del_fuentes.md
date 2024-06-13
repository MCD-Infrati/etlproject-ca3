# 5 Conexión de las fuentes

En este escenario de integración tenemos 3 fuentes de datos diferentes, cada una con requisitos particulares que se describen a continuación.

## 5.1 Archivo CSV
    Se recibió un archivo en formato .CSV (Comma Separated Values), para esta fuente de información se utilizó un objeto con las siguientes características:

     *- Objeto Pentaho:*  CSV File Input  
     *- Delimitador:* El archivo utiliza el punto y coma (;) como delimitador de campos.
     *- File encoding:* La codificación utilizada es UTF-8.
     *- Validación del contenido:* Se utilizó Notepad ++ para validar el contenido del archivo


## 5.2 Mongo DB 
    Recibimos el link de conexión a una base de datos de Mongo en la nube, a un clúster llamado Infrati. Dentro de este se encuentra la Base de Datos Test donde están las tablas que se desean leer, con las siguientes características:

     *- Objeto Pentaho:* Se utilizó MongoDB Input
     *- Connection String:* El proporcionado que nos da acceso a la BD (Por seguridad no se agrega el link)
     *- Database:* test
     *- Collection:* bsmt, garage, pool, misc (Para cada colección fue necesario construir un objeto Mongo DB Input).
     *- Validación del contenido:* Se utilizo Mongo DB Compass

El usuario de conexión a la Base de Datos no tenía los privilegios suficientes para crear vistas que permitieran realizar una única conexión que extrajera todos los datos.

## 5.3 PostgreSQL
    En elephantSQL se nos brindó la oportunidad de crer un esquema par alojar una Base de Datos, de la cual recibimos los Scripts de creación y de carga de datos, una vez creada el esquema y cargada la información realizamos la conexión a nuestro proyecto de Pentaho con las siguiente características:
     
     *- Database Connection:* Se creo una conexión llamada BD_CA3 PostgreSQL, donde:
        **- Connetion Type:** PostgreSQL
        **- Access:** Native (JDBC)
        **- Hostname/Database Name/Username/Password:** Los que se obtienen desde la ventana de atributos del esquema creado y que consultamos desde elephantSQL.
     *- Objeto Pentaho:* Table Input
     *- SQL:* Se realizó un select * de la vista creada en Elephant con los datos del proyecto.
     *- Validación del contenido:* Se utilizo SQL Browser desde ElephantSQL, adicionalmente se utilizó pgAdmin 4 v4.8 que mantiene una UX mas amigable desde donde se crearon las vistas requeridas.
