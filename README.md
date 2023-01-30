# Design-automation-Autocad-Electrical

Este repositorio comtempla una propuesta, la cual premite haciendo uso de la programación disminuir los tiempos de diseño En Autocad Electrical. Para esto se hace un algoritmo el cual se divide en dos partes que son la creación de copias de cada uno de los módulos y cambio de componentes.

<p align="center">
    <img src="https://github.com/amalzatev/Design-automation-Autocad-Electrical/blob/main/Imagen8.png" alt="Logo">
</p>



# Creación de copias

Inicialmente, se hace la copia de los diseños para el caso trabajado en este caso, para esto se debe seguir la metodología mostrada a continuación:

1. Para lograr la automatización se deben generar unos archivos maestros que serán la base para el código, este archivo debe contener elementos como lo son la alimentación para las RTU, alimentación, calefacción y tomas, la HMI, un módulo de entradas análogas, un módulo de 24 V, un módulo de 125 V, y un módulo de salidas.
2. Se debe tener claro el número de módulos para cada caso, el código de la subestación, si se implementara HMI y la dirección en donde se quieren guardar las copias.
3. Con los pasos anteriores se hacen las copias de cada módulo y elemento de los diagramas esquemáticos.

En general estos deben ser los pasos que se deben seguir para la copia de los planos. Es importante tener en cuenta que de acuerdo al número de Rack los editables que corresponden a la alimentación pueden cambiar, por lo tanto se debe tener cuidado en los casos en que se tengas muchos varios Rack.

# Configuración de componentes

Aprovechando una de las herramientas que nos brinda Autocad Electrical, la cual nos permite hacer la exportación de los componentes que tiene todo el proyecto en un archivo de Excel, se crea otro ejecutable que genera este archivo para que al ser importado el nombre de cada modulo sea cambiado de manera automática. 

1. El programa recibe estos archivos y para cada uno de acuerdo a la familia del componente hace el cambio según corresponda el número del módulo.
2. Después de tener el DataFrame con la configuración para todo el proyecto, se crea un archivo de Excel con la misma forma que se exportaron los archivos en el primer paso.
3. En este caso ya se tienen dos archivos de Excel, uno para las entradas tanto de 24 como de 125 y uno para las salidas, los cuales deben ser importados para de este modo cambiar los nombres de borneras y módulos.

Hasta este punto se tienen todos los dibujos del proyecto con su respectivo nombre para cada módulo.

# Configuración de los destinos

Otro de los procesos que requieren de tiempo es el de los direccionamientos, por lo tanto, se trata de que esto sea un poco más automático, es por esto que una parte del código para la configuración de componentes crea el archivo que corresponde a los direccionamientos tanto de orígenes como destinos para todos los módulos.

1.  Los módulos que serán copiados son creados con Sigcodes que permitan la automatización para los demás slot.
2.  Después de hacer las copias se exporta el archivo de Excel desde Electrical que corresponde a los códigos (Sigcode) de los direccionamientos.
3.  Desde el programa se crea el archivo que debe ser importado para cambiar los Sigcode de tal manera que sea único para cada origen - destino.
4.   Por último, desde el Autocad Electrical se actualizan todos los direccionamientos después de ser cargados al proyecto.




