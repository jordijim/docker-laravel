
## Estructura y configuración Docker para Laravel

Primero hay que clonar en proyecto Laravel en la ruta elegida:

~~~
git clone https://github.com/laravel/laravel.git docker-laravel
~~~ 

En la ruta ~/www/docker-laravel ejecutamos un contenedor Composer en Docker para instalar dependecias.

~~~
docker run --rm -v $(pwd):/app composer install
~~~

Le damos permisos no-root al directorio

~~~
sudo chown -R $USER:$USER ~/laravel-app
~~~
