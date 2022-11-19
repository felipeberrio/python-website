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