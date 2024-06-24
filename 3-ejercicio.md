## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es /var/lib/mysql
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
Está vacía.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name msqlContainer --network net-wp --env-file=variablesEntorno.env -v B:/Docker:/var/lib/mysql mysql:8
```
### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Se encuentran los volumenes creados a partir de la imagen msql.


### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
```
docker run -d --name wordpressContainer --network net-wp --env-file=variablesEntorno.env -p 9500:80 -v B:/Docker/WORDPRESS:/var/www/html wordpress
```
### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
La personalizacion, al igual que en el ejercicio anterior, se mantiene intecta ya que se guarda en el host la parte del contenedor que se ha guardado como parte de volumen.


