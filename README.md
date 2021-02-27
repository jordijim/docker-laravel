
## Estructura y configuración Docker para Laravel

Primero hay que clonar en proyecto Laravel en la ruta elegida:
~~~
git clone https://github.com/laravel/laravel.git docker-laravel
~~~ 

Copiamos los archivos de este repo dentro de la ruta elegida.

En la ruta ~/path/docker-laravel ejecutamos un contenedor Composer en Docker para instalar dependecias:
~~~
docker run --rm -v $(pwd):/app composer install
~~~

Le damos permisos no-root al directorio
~~~
sudo chown -R $USER:$USER ~/laravel-app
~~~

Duplicamos el .env de Laravel y configuramos
~~~
cp .env.example .env
~~~

Levantamos los contenedores
~~~
docker-compose up -d
~~~

Generamos la Key de Laravel
~~~
docker-compose exec app php artisan key:generate
~~~

Y por último rehacemos la cache de la configuración
~~~
docker-compose exec app php artisan config:cache
~~~

###Otra info
Comando para ejecutar npm del servicio npm
~~~
docker-compose run --rm npm install
docker-compose run --rm npm run dev
~~~

Si hay problemas de npm a la hora de instalar o run dev, revisar permisos carpeta node_modules.