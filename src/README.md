# Python-website

### Comenzando nuestro proyecto

1. Creamos nuestro primer archivo index.py donde crearemos el sitio web con un framework que es mas practico en lugar de puro python. Existen dos frameworks más populares FLASK y DJANGO, ambos son frameworks con distinto enfoque que permite crear tu aplicaicón web, Flask es más sencillo, Django es más preparado que deja todo listo en el sitio web.

### FLASK

https://flask.palletsprojects.com/en/2.2.x/

2. Vamos a la documentación de FLask, y dice que podemos instalarlo con pip (el administrador de paquetes de python), abrimos una terminal en el proyecto e instalamos: pip install Flask, instalamos el paquete Flask desde internet para el proyecto (computador tambien) a partir de ahora ya podemos importar flask

3. Importamos flask a nuestro index: from flask import Flask

4. Vamos a inicializar el framework flask, por lo que lo usamos como un método que le entrega la variable que nos brinda python: __name__; esto para confirmar que ese va a ser el archivo principal de la aplicación donde va a arrancar: Flask(__name__) y la vamos a guardar en una variable para usar la app para conectar las rutas del servidor y demás
    app = Flask(__name__)

5. Para crear una ruta vamos a usar primeramente un decorador y la variable con el metodo route: 
            @app.route('/')

6. Cuando un usuario entre a la ruta /, voy a manejarlo con una función que defino ahí mismo llamada home que va a retornar un primer hello world
            @app.route('/')
            def home():
            return 'hello world'

7. Para un servidor o nuestro servidor local temporal ,queremos que este escuchando siempre por lo cual tenemos que configurar la conexión.
    Vamos primeramente a comprobar que estemos en el archivo principal para ver que lo ejecutamos como un archivo y no como si fuera un modulo:
    if __name__ == '__main__':

8. Ya podemos ejecutar el metodo de ejecucion de la app run: 
    app.run()

9. Para ejecutar nuestro archivo vamos a escribir en consola: python index.py

### Crear otras rutas

10. Vamos a modificar del objeto app para crear una nueva ruta
        @app.route('/about')
        def about():
            return 'About Page'

11. Nosotros realmente no queremos retornar texto, queremos realmente retornar un archivo Html para maquetear páginas web por lo que vamos a crear una carpeta que almacene los HTML que vamos a crear (/templates) y crearemos el archivo home.html

12. Para poder importar los templates que vamos creando, en index.py vamos importar otra libreria de FLask llamada render template: from flask import Flask, render_template

13. Vamos a introducir nuestro template en la ruta creada a la app: 
        @app.route('/')
        def home():
            return render_template('home.html')
            }

14. Creamos la estructura básica del home.html y un texto base para comprobar la conexión

### Debug mode one - Modo prueba on para que se reactualice el servidor al modificar

15. Para no tener la necesidad de cerrar el servidor y reiniciarlo siempre, podemos agregar una parte de código que va a hacer que la app se ejecute en modo de prueba por lo cual se encuentra cambiando archivos y cosas asi que se reiniciara cada vez que se cambie el código:
        if __name__ == '__main__':
        app.run(debug=True)

### Creamos demás rutas y templates del sitio web

16. Creamos y vinculamos la ruta about

>A veces el computador guarda memoria cache de los archivos, por lo qeu podemos usar Ctrl + Shift + R o modo incognito para inciiar sin cache y que si se actualice por completo

### Creando estilos

17. Creamos una nueva carpeta llamada Static afuera del todo donde vamos a colocar nuestros archivos estaticos, es común el nombre pero no obligatorio

18. Creamos la ruta static/css/main.css y agregamos estilo al fondo y unínmos en el archivo html, esto con la etiqueta link y unas llaves en href, para que sepa que vamos a ubicarlo con python una especie de función brindada por python para usar los estilos de la carpeta estatica

    <link rel="stylesheet" href="{{ url_for('static', filename='css/main.css') }}">

### Utilizando librerias de estilos/frameworks como bootstrap

19. Importamos según la documentación el archivo el link para html y vamos a crear el navbar del home

### Motores de plantillas

20. Para reutilizar código vamos a usar motores de plantillas para repetir por ejemplo el navbar en about, creamos un archivo llamado layout.html en templates

21. PAra el layout copiamos toda la documentación del home.html y solo ponemos 

    <section>
        {% block content %}
        {% endblock %}
    </section>

    Juesto en la sección que va a ser única para cada bloque ya que lo demás se va a repetir

22. ya podemos borrar toda la estructura html del home y usar solo lo que vamos a mostrar: 
<h1>Home Page</h1>
<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolor consequuntur laborum modi nam ullam sequi nostrum aspernatur ipsum ipsam quam dolores impedit placeat, beatae sit adipisci incidunt sint id quasi officiis labore neque voluptatibus, atque pariatur. Vel, rerum adipisci dignissimos obcaecati sint et id temporibus totam ducimus. Architecto, quibusdam illo.</p>


23. Para que utilice el otro codigo del motor de plantillas vamos a incluir este extend: 

{% extends "layout.html" %}    

{% block content %}
<h1>Home Page</h1>
<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Dolor consequuntur laborum modi nam ullam sequi nostrum aspernatur ipsum ipsam quam dolores impedit placeat, beatae sit adipisci incidunt sint id quasi officiis labore neque voluptatibus, atque pariatur. Vel, rerum adipisci dignissimos obcaecati sint et id temporibus totam ducimus. Architecto, quibusdam illo.</p>
{% endblock %}

24. Cambiamos estilos con bootstrap agregando un jimbotron

25. agregamos un fondo con el sitio web: iugradientes.com para que se puedan ver los tipos de fondo en gradiente con su código

26. Para que nos tome bien los contenedores nuestros bloques de codigo vamos a incluirlos en un div

    <div class="container p-4">
        {% block content %}
        {% endblock %}
    </div>

### Crear entorno virtual

26. Para preparar nuestro código y desarrollar un sitio web, es mejor tener un entorno virtual: el cual es un entorno que separa nuestro proyecto de cualquier otro proyecto de python desarollado antes. esto funciona con administradores de paquetes. Por lo cual vamos a guardar todo nuestro código en /src.

27. Vamos a crear nuestro entorno virtual en: python virtual env; para instalarlo vamos a usar en el terminal el siguiento módulo: pip install virtualenv

>Ya instalamos virtual env vamos a crear el entorno virtual
28. Para comenzar a ejecutar el entorno virtual desde python un módulo vamos a usar en la terminal y con un nombre que sera venv: python -m venv venv

> Se comienza a instalar venv en la carpeta venv con lo mas importante los scriptsdonde nosotros vamos a tener comando de python3 python pip y demas para ejecutar únicamente con este proyecto en su entorno virtual, desde la consola podemos usar estos scripts desde nuestro entorno
> Si vamos a cd venv/scripts, podemos ejecutar: python y podemos ver que usamos la verción 3.10 de python en la maquina virtual - podemos cancelar con: exit()

29. vamos a instalar flask desde nuestro entorno virtual desde la carpeta de scripts: C:\Users\pipe_\Documents\GitHub\python-website\venv\Scripts>pip install flask
> Se va a instalar flask en nuestro entorno virtual, ya esta el modulo flask

30. Ejecutamos python desde scripts pero subiendo el nivel: C:\Users\pipe_\Documents\GitHub\python-website\venv\Scripts>python ../../src/index.py
>Ejecutaoms el index pero desde el python del script de nuestra maquina virtual

### Desplegar la app en Heroku

31. Heroku nos permite montar nuestra aplicación sin la necesidad de configurar un servidor y demás; vamos a Heroku.com y nos loggeamos

32. Vamos a descargar Heroku CLI para poder ejecutar heroku desde nuestro terminal: https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli

33. Comprovamos nuestra instalación desde una nueva consola, con: heroku --version

34. Lo primero es comenzar a loggearnos en Heroku: heroku login, el cual nos llevara con un boton al navegador a logearnos

35. Configuramos lo que necesitamos la aplicacion ademas del entorno virtual: Heroku necesita 1) Archivo de necesidades de heroku de nuestra app: src/requirements.txt
2) Crear archivo de ejecución donde indicamos el entorno de python de nuestra app, por defecto el tomara la versión python3.6 o creamos archivo con: src/runtime.txt
3) Crear archivo: Procfile para decir que archivos tiene que ejecutar al iniciar

>Nosotros no solamente ejecutaremos la biblioteca FLASK, sino que heroku tambien va a utilizar la biblioteca: Gunicorn que es un complemento que necesita Heroku para poder ejecutar nuestro servidor HTTP

36. Instalamos biblioteca Gunicorn con: pip install gunicorn desde Scripts nuestro entorno virtual: C:\Users\pipe_\Documents\GitHub\python-website\venv\Scripts>pip install gunicorn

37. En procfile especificamos

Vamos a ejecutar una pagina web, con gunicorn, el archivo index con el nombre app de nuestra aplicacion web:
web: gunicorn index:app

38. Usamos python --version en scripts de nuestro entorno para ver la versión que tiene para ponerla en el archivo runtime.txt

39. Usamos el modulo: pip freeze para ver todo lo que necesita nuestra aplicación y lo vamos a agregar a requirementes.txt con un comando: C:\Users\pipe_\Documents\GitHub\python-website\venv\Scripts>pip freeze > ../../src/requirements.txt

Con esto ya podemos desplegar nuestra aplicación

40. Creamos nuestra aplicación con heroku en la terminal con: heroku create // o con heroku create NOMBREDELPROYECTO

Nombre aleatorio nuestro: vast-scrubland-58534

41. Vamos a crear un repositorio remoto en heroku a partir de un repositorio remoto en Git - no necesita ser github: https://devcenter.heroku.com/articles/git

Enlazamos heroku a Git
heroku git:remote -a vast-scrubland-58534

Subimos nuestra rama
git push heroku main




