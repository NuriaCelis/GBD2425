# UNIDAD 1. SISTEMAS DE INFORMACIÓN

## 1.- FICHEROS

Un ordenador almacena muchos tipos de información. Toda esta información está almacenada en los dispositivos de almacenamiento del ordenador. Para poder organizar toda la información, se utilizan ficheros o archivos. 

Los ficheros son estructuras de información que crean los sistemas operativos de los ordenadores para almacenar datos. Suelen tener un nombre y una extensión, que determina el formato de la información que contiene.

### 1.1.- Tipos de ficheros y formatos

El formato y tipo de fichero determina la forma de interpretar la información que contiene. Un fichero es una ristra de bits (ceros y unos), de forma que es necesaria su interpretación para dar sentido a la información que almacena. 

Tradicionalmente, los ficheros se han clasificado de muchas formas. Vemos una clasificación de los ficheros en función de varias categorías.

1. **Según el contenido:** 
   - _Ficheros de texto_: el contenido del fichero lo traduce el sistema operativo a caracteres alfabéticos y números que entiende el ser humano.
   - _Ficheros binarios_: el contenido del fichero no se traduce directamente. Son una serie de bits que almacenan sonido, video, imágenes, etc...

2. **Según la organización:** Dicta la forma en la que se acceden los datos.
   - _Ficheros con organización secuencial_: Los datos estan dispuestos siguiendo una secuencia ordenada, es decir, los datos estan unos detrás de otros. Para acceder a un dato concreto, se han de recorrer todos los datos anteriores. 
   - _Ficheros de organización directa_: permiten acceder a un dato en concreto sin necesidad de acceder a los anteriores. 
   - _Ficheros de organización indexada_: acceden a los datos consultando un índice, es decir, una estructura de datos que permite acceder a la información rápidamente, simulando la forma en que el índice de un libro facilitaq el acceso a los contenidos. 

Existen variantes de las anteriores que mezclan las mejores características de cada una de ellas.

3. **Según la utilidad:** indica el uso que se va a hacer de el fichero. 
   - _Ficheros maestros_: Si va a contener datos fundamentales para la organización. Por ejemplo, un fichero con los datos de los alumnos de un instituto.
   - _Ficheros de movimientos_: Se almacenan las variaciones de los ficheros maestros.
   - _Ficheros históricos_: Almacenan los datos que ya no son necesarios para su proceso diario.

![Clasificación de ficheros](img/Ficheros.png)

**Realiza los siguientes ejercicios:**

1. Busca en tu ordenador un fichero con extensión docx y ábrelo con el bloc de notas. ¿Porqué no se ve bien el contenido del fichero?.
2. Conectate a Internet y busca una tabla de códigos ascii de 8 bits. Observa las siguientes características:
    - Los 32 primeros caracteres, se llaman caracteres no imprimibles y se utilizaban tradicionalmente para el control de transmisiones.
    - La distancia entre mayúsculas y minúsculas es exactamente de 32 caracteres.
3. La siguiente imagen es una captura de una carpeta en el sistema Windows. Indica de que tipo es cada fichero y que contiene.

![Lista de ficheros](img/Lista.png)

## 2.- BASES DE DATOS

Una **Base de datos**  es un conjunto de datos estructurados que pertenecen a un mismo contexto y, en cuanto a su función, se utiliza para administrar de forma electrónica grandes cantidades de información.

Anteriormente a las bases de datos, se utilizaban ficheros tradicionales, como los que hemos visto en el apartado anterior. Veamos según su definición cuales son sus diferencias.

- Los _ficheros tradicionales_ almacenan los datos en archivos individuales, exclusivos de cada aplicación en particular. Los datos de un fichero no están relacionados con datos de otros ficheros. Son unidades independientes. En este sistema, los datos pueden ser redundantes y la actualización de los datos es más lenta.
- Las _bases de datos_ tienen el almacenamiento de datos formalmente definido, controlado centralmente para intentar servir a múltiples y diferentes aplicaciones. La base de datos es una fuente de datos que son compartidos por numerosos usuarios para diversas aplicaciones.

Así, en un sistema de ficheros tradicional, la información está dispersa en varios ficheros de datos y existe un cierto número de programas que los recuperan y agrupan. Aunque los sistemas de ficheros o archivos supusieron un gran avance sobre los sistemas manuales, tienen inconvenientes bastante importantes que se solventaron, en gran medida, con la aparición de los sistemas de bases de datos.

### 2.1.- Tipos de bases de datos

Coincidiendo con la evolución histórica de las bases de datos éstas han utilizado distintos modelos:

- Jerárquicos: La estructura jerárquica fue usada en las primeras bases de datos, donde las relaciones entre los distintos datos almacenados forman una estructura de árbol.
- En red: La estructura en red contiene relaciones más complejas que las jerárquicas. Adminte relaciones de cada registro con varios que se pueden seguir por distintos caminos.
- Relacionales: La estructura relacional es la más extendida y es la que vamos a estudiar nosotros. Almacena los datos en filas o registros y columnas o campos. EStas tablas estarán relacionadas entre sí por claves comunes.
- Multidimensionales: La estructura multidimensional se parece a la del modelo relacional, pero en vez de las dos dimensiones fila-columna, tiene N dimensiones. Ofrece el aspecto de una hoja de cálculo.
- De objetos: la estructura orientada a objetos está diseñada siguiendo el paradigma de los lenguajes orientados a objetos. De este modo soporta los tipos de datos gráficos, imágenes, voz y texto de manera natural. Esta estructura tiene gran difusión en aplicaciones web para aplicaciones multimedia.

Otro modo de clasificar las bases de datos es según su ubicación. Veamos las más importantes:

- Bases de datos locales. En modo local tenemos la base de datos y el usuario ubicados en el mismo ordenador. Un ejemplo de base de datos que funciona en modo local es Microsoft Access, que es una base de datos fácil de manejar por usuarios poco expertos que funciona bien en modo local y mientras no tenga que albergar grandes cantidades de información.
- Bases de datos centralizadas. En los sistemas centralizados tenemos la base de datos completa en un mismo servidor, y todos los usuarios acceden a ese servidor. Que la base de datos esté en un mismo servidor no implica que esté en un solo archivo o en el mismo disco, puede estar repartida.En modo Cliente/Servidor, la base de datos se encuentra en un ordenador (el Servidor) y los usuarios acceden simultáneamente a esa base de datos a través de la red (sea una red local o Internet) desde sus ordenadores a través de un programa Cliente. A nivel de empresas es el sistema que más se utiliza en la actualidad.
- Bases de datos distribuidas. Tenemos la información repartida en distintas localizaciones unidas todas ellas mediante red y un sistema gestor de bases de datos distribuidas. Las distintas localizaciones suelen ser distintas geográficamente.

![Clasificación de las bases de datos](img/Bases.png)

**Realiza los siguientes ejercicios:**

1. Busca por Internet las ventajas y desventajas de utilizar un sistema de ficheros tradicional frente a un sistemas de bases de datos para almacenar información.
2. Busca por Internet un esquema o imagen que te ayude a identificar cada uno de los tipos de datos de las bases de datos que hemos visto.
