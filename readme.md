# Descripción general del proyecto

En este proyecto hemos realizado una agenda en php y symfony para visualizar nuestros contactos, tanto **personales** (*amistades*) como **profesionales** (*trabajo*). Además, hay una agenda general en la que se incluyen todos los contactos guardados.

En nuestra agenda podremos realizar las siguientes operaciones:
* Visualizar contactos
* Crear contactos
* Borrar contactos
* Modificar contactos
* Guardar contactos

También tiene una manera sencilla de desplazarse por el proyecto y es responsive.

-----------------------

# Como se usa el proyecto
Al abrirlo, se despliega la página principal del proyecto.

![Agenda](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/markdownAgendaImagen.png)
Comentaré brevemente por partes la agenda para después poder profundizar en como utilizarla al completo:

El **encabezado** contiene el título de la agenda y dos botones, uno para **agregar contactos** y otro para volver al inicio (o de **retorno**).  

El **cuerpo** incluye dos iconos que hacen referencia a la agenda **personal** o **profesional**. Clicando en sus nombres o en los propios iconos te redirigirá a otra página con sus datos respectivos.

En el **footer** se encuentran los iconos respectivos de las **redes sociales** (instagram, twitter y facebook).    
Además, se incluye una marca de agua con la que hago referencia al **autor** (Javier Debén Chacón).

Ahora profundizaremos más en cada una de sus partes:
* **Encabezado:** El botón de volver siempre nos devolverá a la página principal. Al clicar en el botón de agregar, se desplegará una nueva página en la que podremos añadir datos y guardarlos para crear un usuario nuevo.
![AgregarContacto](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/agregarcontct.png)
    ~~~
    Nota: Si no se completa la información requerida, saltará un mensaje de error el cual pedirá que    
    cubras todos los datos para poder guardar el contacto.
    ~~~
    ![Error](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/error.png)
- - -
* **Cuerpo:** Al clicar en una de las agendas, desplegarán sus contactos guardados en una nueva página.
    ![Contactos](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/contactosagendaa.png)
    Al clicar en uno de estos, mostrará toda la información guardada del contacto y añadirá la opción de **modificar** el contacto junto con la de **borrar** el contacto.
    ![Info](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/info.png)

* **Footer:** En esta parte se muestra al creador de la página y su email. A la derecha se incluyen tres iconos con sus respectivos accesos directos a las redes sociales (Instagram, Facebook y twitter).
    ![footer](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/footerfoto.png)



--------------

# Requisitos del entorno de desarrollo

Para el desarrollo de este proyecto no se necesitan equipos de altas prestaciones, es suficiente con cualquier ordenador medianamente actual. No hay requisitos de potencia específicos, con tener un procesador de al menos dos núcleos y 4GB (recomendables 8GB para mayor fluidez del sistema). El sistema operativo puede ser cualquiera de los habituales (Windows, Linux, MacOs X) ya que para todos ellos hay disponibles las herramientas o variantes que detallaremos a continuación:

Editor de texto: Nos valdría cualquier editor de texto plano pero recomendamos y nosotros utilizamos un editor de código fuente como Visual Studio Code. Este software nos permite resaltar el código, refactorizarlo, identarlo, de tal forma que se nos facilita mucho su legibilidad. Así mismo nos ayuda con la integración con Git. 

Para probar en local necesitamos una base de datos MySQL, que en nuestro caso utilizamos la integrada en el paquete XAMPP.

Para finalizar, necesitamos tener instalado en nuestro equipo el software de PHP y de Symfony, usando el Composer como gestor de paquetes de PHP.

-------------

# Guía de instalación y funcionamiento
Tanto para desarrollar como para ejecutar nuestro proyecto necesitamos aplicaciones de software sobre las que ejecutar nuestra agenda. En primer lugar necesitamos instalar el intérprete de [PHP](https://www.php.net/downloads) ya que es el lenguaje de programación en el que desarrollamos nuestra práctica y el [Composer](https://getcomposer.org/download/) como gestor de paquetes para posteriormente obtener symfony, los cuales podemos descargar desde las páginas web oficiales ya enlazadas. Así mismo necesitamos una base de datos en la que almacenar el contenido de nuestra agenda y para ello vamos a usar la integrada en el paquete [XAMPP](https://www.apachefriends.org/download.html), la cual es una MySQL.

Una vez tenemos este software básico instalado, procederemos a instalar el framework de Symfony. Para ello necesitamos tener el PHP en las variables de entorno y teclearemos en una consola (cmd) lo siguiente:
`c:\> php -r "readfile('http://symfony.com/installer');" > symfony`

Tras esto hay que instalar Doctrine. Este paquete nos ayuda a crear tanto entidades como repositorios de forma sencilla, a la vez que las tablas en la BBDD y realizar el mapeo de forma automática y coherente. Para lo cual teclearemos:
`composer require symfony/orm-pack`
`composer require --dev symfony/maker-bundle`

Una vez tenemos todo el software instalado vamos a crear nuestro proyecto. Para ello teclearemos:
`symfony new --full agendaSymfony`

Abrimos el proyecto con el Visual Studio y editamos el archivo .env para configurar el acceso a la BBDD (la cual tendremos que tener lanzada y configurada desde XAMPP):
`DATABASE_URL="mysql://root:1234@127.0.0.1:3306/agendaSymfony?serverVersion=5.7"`

Se puede crear la base de datos directamente con Doctrine con el siguiente comando:
`php bin/console doctrine:database:create`

Tras esto, se pueden añadir migraciones y "fields" dentro de la base de datos con el siguiente comando:
`php bin/console make:entity`
~~~
Nota: Tras esto, se desplegará una serie de comandos como estos, los cuales tendrás que completar
dependiendo de la información que quieras guardar:
~~~
![](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/Entidad%20contacto1.png)
![](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/Entidad%20contacto2.png)
![](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/Entidad%20contacto3.png)

Una vez tenemos creada la entidad, podemos hacer que sea el propio Symfony quien nos cree la tabla correspondiente en la base de datos o nos actualice la existente si la hemos modificado. Para ello, hemos de teclear lo indicado en la última captura al terminar de crear la entidad:
`php bin/console make:migration`

Finalmente, despues de introducir toda la información necesaria, podemos crear el controller, que nos da las operaciones básicas del CRUD (Create, Read, Update, Delete), por medio del comando:
`php bin/console make:controller ProductController`

Con esto tendríamos el esqueleto del proyecto creado, tras eso tendríamos que trabajar editando y creando código de forma manual.

----------------

# Tecnologías utilizadas
| Tecnología | Ámbito | Explicación | 
| ---- | ---- | ---- |
| HTML | Lenguaje de marcas | Utilizado para definir la estructura y los contenidos visualizados en el navegador web por el usuario. Con este lenguaje se define como se estructuran sin influir en su diseño lo cual actualmente se realiza mediante la siguiente tecnología. |
| CSS | Lenguaje de estilos | Usado para darle formato visual a los contenidos mostrados en el navegador. Nos referimos tales como formato visual a cuestiones como colores y tamaños de tipografía, colores de fondo y de los diversos componentes, enlaces (pulsados y sin pulsar)... Simplemente cambiando esta hoja de estilos se podría modificar el diseño visual del contenido desplegado. |
| PHP | Lenguaje de programación | Es el lenguaje utilizado en el proyecto para realizar nuestro *core* o **backend**, es decir, toda la operativa de nuestro proyecto. Es el lenguaje a través del cual realizamos las operaciones necesarias para el funcionamiento de la agenda, esto es, la recuperación de datos solicitados por el usuario y que serán mostrados en la *vista* o **frontend**, el guardado de las nuevas entradas de la agenda con sus correspondientes comprobaciones necesarias. |
| Symfony | Framework web | Framework web basado en PHP que implementa el patrón Modelo-Vista-Controlador **MVC**. Nos ayuda y facilita en las tareas de escuchar los diferentes endpoints (urls) y mapearlas a los correspondientes métodos que realizan las funciones que implementan el comportamiento buscado para esa operación y que están escritas en PHP. Tambíen nos ayuda a trabajar con las entidades que representan los datos almacenados en nuestra BBDD, así como los repositorios que nos permiten acceder y consultarlos de forma sencilla. |
| Twig | Motor de plantillas | Es el motor por defecto utilizado por Symfony y que nos ayuda a generar el HTML de forma dinámica para ser enviado a la vista. El contenido de este HTML va a ser función de la consulta que nos devuelva la BBDD. En esta plantilla se define un esqueleto del HTML que será rellenado en cada ejecución con los datos correspondientes enviados por el controlador despues de consultar al modelo. |

---------------

# Autor o autores

| Nombre | Apellidos | Email | Centro |
| ------ | ------ | ------ | ------ |
| Javier | Debén Chacón | Jdchacon99@gmail.com | Liceo la Paz |

-----

# Licencia

#### Reconocimiento-CompartirIgual
#### CC BY-SA
 ![Info](https://raw.githubusercontent.com/jadec99/Images4Markdown/main/CC.png)
 
Esta licencia permite que otros mezclen, adapten y desarrollen sobre su trabajo incluso con fines comerciales, siempre que le otorguen crédito y licencian sus nuevas creaciones bajo los mismos términos. Esta licencia a menudo se compara con licencias de software de código abierto y gratuitas "copyleft". Todos los trabajos nuevos basados en el suyo llevarán la misma licencia, por lo que cualquier derivado también permitirá el uso comercial. Esta es la licencia utilizada por Wikipedia y se recomienda para materiales que se beneficiarían de la incorporación de contenido de Wikipedia y proyectos con licencias similares.

-------

# Como contribuir al proyecto

Con la licencia seleccionada, cualquiera podría contribuir y trabajar en el proyecto añadiendo funcionalidades o mejorando su usabilidad siempre y cuando la licencia sea respetada para que siga siendo así. Se sugieren como líneas de **mejora**:
1. Mejorar la navegación a traves de la aplicación de tal forma que el botón volver te lleve a la pantalla anterior en vez de al inicio. 
2. Incluir más datos en los registros guardados:
    - Direcciones
    - Varios teléfonos (móvil y fijo)
    - Disponibilidad horaria
3. Una agenda general en la que se pudiesen visualizar todos los contactos independientemente de su tipo (personal o profesional).

