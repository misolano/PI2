* Instituto Tecnológico de Costa Rica
* Interfaces Graficas de Usuario
* Prof: Armando Arce
* Estudiantes: Oscar Rodríguez Corrales, Milagro Solano Fonseca

##Introducción##
Los mapas conceptuales son útiles en la representación y compresión de materia sobre algún tema o temas en específico, muchas veces usados por estudiantes o trabajadores para resumir información útil, la cual acomodada de cierta manera es representativa visualmente y puede ser comprendida y recordada de mejor manera.
El presente proyecto pertenece al curso de interfaces graficas de usuario, se busca conocer maneras de representar y desplegar diversos tipos de información (mapas conceptuales, gráficos, diagramas) mediante la herramienta xulRunner. Además, se pretende implementar librerías javascript mediante código coffeescript unido con xul y asi, contar con nuevas maneras de mostrar imágenes y datos en páginas web.
La herramienta xulRunner consiste en un entorno de tiempo de ejecución creado por la Fundación Mozilla para ofrecer un back-end común para las aplicaciones creadas mediante xul, aunque todavía se encuentra en etapa de desarrollo. 

##Descripción del contenido a desplegar##

###Librería Joint.js###

JointJS es una librería de JavaScript utilizada para la creación de diagramas o mapas conceptuales, estos diagramas pueden ser creados completamente interactivos. Esta librería permite la implementación de herramientas de edición de mapas conceptuales o simplemente la visualización d estos.
Las principales características con las que cuenta la librería son:

* Conexión de objetos con varios tipos de líneas.
* Interacciones con conexiones y objetos.
* Controladores personalizados para diversos eventos.
* Líneas curvadas suavizadas.
* Elementos listos para usar de diagramas ya conocidos (ERD, FSA, UML, LDM).
* Diagramas jerárquicos.
* Serializacion.
* Extensible.
* Personalizable.

Dicha librería es soportada por los siguientes navegadores Firefox 3.0+, Safari 3.0+, Opera 9.5+, Google Chrome 4+ e Internet Explorer 6.0+.
JointJS hace uso de RaphaelJS, pequeña librería JavaScript que permite la simplificación de trabajo con vectores gráficos en el campo web.  Esta librería utiliza recomendaciones SVG W3C y VML como base en la creación de gráficos. Debido a esto, cada objeto grafico creado es también catalogado como un objeto DOM, de esta manera se pueden agregar eventos manejables    JavaScript o modificarlos luego. Esta librería también es compatible con los navegadores antes especificados.
Como se mencionó anteriormente, la librería JointJS puede ser utilizada para la creación de diversos diagramas relacionados con diferentes ámbitos que necesitan resumir o interpretar información. A continuación se presentan ejemplos de diagramas que pueden ser creados mediante la utilización de la librería:

####Ejemplos####

http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/imagen1.jpg


Así, el diagrama anterior puede ser diseñado mediante figuras y líneas creadas mediante el siguiente código:
title('Entity-relationship diagram.');
description('Make your database structure visible.');
dimension(800, 250);

Definición del espacio en el que se dibujara el diagrama:

    var erd = Joint.dia.erd;
    Joint.paper("world", 800, 250);

Creación del cuadrado que tiene la etiqueta “Entity”

    var e1 = erd.Entity.create({
    rect: { x: 220, y: 70, width: 100, height: 60 },
    label: "Entity"
    });
    
Creación del rombo que contiene la etiqueta “Relationship”

    var e2 = erd.Entity.create({
    rect: { x: 520, y: 70, width: 100, height: 60 },
    label: "Weak Entity",
    weak: true
    });
    
Union de ambas figuras

    e1.joint(r1, erd.toMany);


http://www.ic-itcr.ac.cr/~osrodriguez/Interfaces/imagen2.jpg


El diagrama anterior ha sido creado utilizando el siguiente código:

    title('Finite State Machines');
    description('Give light to your components state transitions.');
    dimension(800, 400);

Define el tamaño de la ventana en la que se dibujara el diagrama:

    var fsa = Joint.dia.fsa;
    Joint.paper("world", 800, 400);

Creación del círculo con la etiqueta “state 1”
    
    var s1 = fsa.State.create({
    position: {x: 120, y: 70},
    label: "state 1"
    });

Creación del círculo inicial

    var s2 = fsa.State.create({
    position: {x: 250, y: 100},
    label: "state 2"
    });

Creación del círculo con la etiqueta “state 1”
    
    var s0 = fsa.StartState.create({
    position: {x: 20, y: 20}
    });

Definición del arreglo con todas las variables

    var all = [s0, s1, s2];

Unión de los círculos de estados mediante las flechas
    
    s0.joint(s1, fsa.arrow).register(all);
    s1.joint(s2, (fsa.arrow.label = "a", fsa.arrow)).register(all);
    fsa.arrow.label = null;  


###Mapas Conceptuales###

####Historia ####

El Doctor Novak es un experimentado Investigador Científico que completó sus estudios superiores en la Universidad de Minnesota en 1958. Enseñó en las Universidades Estatal de Kansas y Purgue y desarrolló los Mapas Conceptuales, como ahora se los conoce, siendo profesor de Educación y Ciencias Biológicas en la Universidad de Cornell, donde realizó investigaciones en educación, aprendizaje, creación y representación del conocimiento. (NOVAK, 2007)

####Concepto####
Los mapas conceptuales (también denominados organigramas) constituyen un eficaz medio para representar gráficamente ideas o conceptos que están relacionados jerárquicamente. El objetivo principal de un mapa conceptual es representar vínculos entre distintos conceptos que adquieren la forma de proposiciones. Mediante este procedimiento aprovecharemos el poder conceptual de las imágenes, facilitando el aprendizaje y el recuerdo de un tema. Desde luego no se trata de memorizar los mapas y reproducirlos en todos sus detalles, sino de utilizarlos para organizar el contenido de estudio. La técnica de elaboración de mapas conceptuales es un medio didáctico poderoso para organizar información, sintetizarla y presentarla. Puede servir para exponer y desarrollar oralmente un tema de manera lógica y ordenada.

####Elementos####

Los mapas conceptuales están compuestos de dos elementos principalmente, los cuales son:
  * Ideas o Conceptos: El mapa conceptual esta hecho de conceptos o ideas, suelen representarse estando encerradas en círculos, óvalos, rectángulos u otra figura geométrica. 
  * Conectores: La conexión o relación entre dos ideas se representa por medio de una línea inclinada, vertical u horizontal llamada conector o línea ramal que une ambas ideas, en muchas ocasiones los conectores van acompañados de palabras de enlace para ayudar  a comprender mejor la relación entre conceptos.

####Usos####

Los mapas conceptuales son muy usados para mostrar información con diferentes propósitos, algunos ejemplos son:
  * Organigramas Corporativos
  * Árboles Lógicos (Binarios, K-arios, etc.)
  * Árboles Genealógicos
  * Resúmenes de Información.

##Definición de estructuras de datos (formato) utilizadas##

Decidimos utilizar archivos de texto en donde se almacenara los datos que representan un mapa conceptual. Como el contenido que se busca desplegar son mapas conceptuales, la manera de representar el o los cuadrados que formaran dicho mapa es mediante la palabra “idea”, seguido de un identificador del cuadrado con el fin de hacer un fácil llamado de este en las conexiones y por último se pone la descripción de lo que se desea que contenga dicho cuadrado del mapa

Además es necesario crear conexiones entre cada uno de los cuadrados que forman el mapa conceptual, para esto se hace uso de la palabra “conectar” seguida de los dos puntos que se desean conectar (de donde inicia la línea, al final de esta).
A continuación se presenta un ejemplo del formato que contendrá dicho archivo:
* idea,g,g
* idea,h,h
* idea,e,e
* idea,b,b
* idea,o,o
* idea,to,to
* conectar,g,h
* conectar,h,o
* conectar,g,e
* conectar,b,e

Una vez que se genera el diagrama anterior, este tendrá la siguiente apariencia:
 
Para el manejo de los comando de creación de diagramas, así como cargar diagramas anteriores y guardar nuevos se utilizara un archivo de texto (.txt) el cual contendrá datos similares a los mostrados anteriormente.

Además de poder mostrar y acomodar diagramas con el formato base,  es posible modificar el tamaño y el color de los cuadros que formaran el diagrama. Para esto se accede a las opciones de menú que nos facilitan estos procedimientos y se ingresan los datos deseados.

Además, una vez que se tiene el mapa conceptual con los cuadros y las conexiones ya establecidos, es posible la modificación de los datos que forman tanto el mapa conceptual como sus características principales (color, tamaño y contenido).

##Forma de compilación, ejecución y utilización de la aplicación##

Para la utilización de la aplicación es posible realizar dos procedimientos diferentes que permitirán ver el contenido y editar los mapas conceptuales. La primera de estas opciones es la utilización de algún browser para abrir la página con el nombre “Index.html”de manera que se despliegue una página normal html, una vez desplegada la página se puede utilizar las opciones de menú disponibles para los mapas conceptuales.

La segunda forma de compilación y ejecución de la aplicación es mediante Adobe Air utilizando las herramientas sdk y adl. La herramienta adl que permite probar la correcta ejecución de las aplicaciones. Esta herramienta se puede ejecutar desde el directorio en donde se instaló el SDK deAdobe Air, por ejemplo: C:/AdobeAirSDK. Por tanto la ejecución se puede realizar de la siguiente forma (desde el directorio tinyhtmleditor\source):

C:\AdobeAirSDK\bin\adl application.xml
Una vez utilizada esta herramienta, en la ventana/editor que se abre se pueden utilizar las opciones de menú, así como interactuar con la creación y manejo de mapas conceptuales.

##Ejemplos de datos a usar como pruebas##

    Prueba #1
    idea,g,g
    idea,h,h
    idea,e,e
    idea,b,b
    idea,o,o
    idea,to,to
    conectar,g,h
    conectar,h,o
    conectar,g,e
    conectar,b,e

 

Prueba #2

    idea,g,g,brown,yellow
    idea,h,h,brown,yellow
    idea,e,e,brown,yellow
    idea,b,b,brown,yellow
    idea,o,o,brown,yellow
    idea,to,to,brown,yellow
    conectar,g,h
    conectar,h,o
    conectar,g,e
    conectar,b,e

 
Prueba #3

    idea,g,g,gray,yellow
    idea,h,h,gray,yellow
    idea,e,e,gray,yellow
    idea,o,o,gray,yellow
    conectar,g,h
    conectar,h,o
    conectar,g,e

 


##Limitaciones observadas y posibles mejoras##

* La utilización de la herramienta Adobe Air junto con la libraría Joint.js presenta algunos problemas de compatibilidad ya que al momento de usar la herramienta provista por dicho entorno la librería para dibujar no funciona de la manera correcta,
* Abode Air y algunas de las funciones creadas para funcionar con dicha herramienta tienen una compatibilidad nula con el despliegue la página como HTML puro, situación que genera una desventaja ya que se obliga al usuario a atarse a un entorno.
* La falta de documentación disponible relacionada con Abode Air y Joint Js dificulta la correcta y fácil utilización tanto de la herramienta como de la librería ya que se hace que la curva de aprendizaje para el uso de ambos sea más grande.
* Una de las posibles mejoras es trabajar los mapas a puro teclado, sin la necesidad de usar el editor de texto para agregar nuevos componentes o modificar algunos ya existentes,
* Otra posible mejora es la posibilidad de agregar y editar el texto directamente en los cuadros de texto gráficos, sin necesidad de utilizar el editor.

