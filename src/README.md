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

### Desplegar la app en Heroku

26. 