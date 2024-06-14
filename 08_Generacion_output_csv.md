## 8. Generación del Output

Una vez que se fusionan todas las fuentes de información se procede a preparar el archivo de salida.

## 8.1 Remover campos no requeridos
Para esto el primer paso que se agrega al proceso es el de remover los campos que no se requieren en el paso posterior, como ya de entrada solo trajimos los campos necesarios, solo los campos PID que se agregaron en el Join son los que se deben remover. Se realizó utilizando el componente Select Values, pero en lugar de seleccionar los que se requieren, excluimos los que no debian considerarse.

## 8.2 Reemplazar los nulos
Una instruccion que tenemos es el reemplazo de los campos nulos, para no tener varios pasos durante el proceso, acá lo dejamos en un único paso para todo el flujo ya que la regla que tenemos aplica de manera general para todos, con el "If field value is null", se indico que si el campo es numero o entero reemplazara el nulo por 0 y en el caso de string se remplaza por NA.

## 8.3 

