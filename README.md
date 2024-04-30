# Proyecto de API en Laravel

¡Bienvenido al proyecto de API en Laravel! Este proyecto está diseñado para explorar diferentes tipos de APIs utilizando el framework Laravel. Aquí encontrarás documentación sobre cómo configurar el proyecto, así como información detallada sobre cada API implementada.

## Configuración del Proyecto

Sigue estos pasos para configurar y ejecutar el proyecto en tu entorno local:

1. Clona este repositorio en tu máquina local:

    ```bash
    git clone https://github.com/tu-usuario/tu-proyecto-laravel.git
    ```

2. Navega al directorio del proyecto:

    ```bash
    cd tu-proyecto-laravel
    ```

3. Instala las dependencias del proyecto utilizando Composer:

    ```bash
    composer install
    ```

4. Copia el archivo de configuración de ejemplo `.env.example` a `.env` y configura tu entorno:

    ```bash
    cp .env.example .env
    ```

5. Genera una clave de aplicación única:

    ```bash
    php artisan key:generate
    ```

6. Configura tu base de datos en el archivo `.env` y migra la base de datos:

    ```bash
    php artisan migrate
    ```

7. Inicia el servidor de desarrollo:

    ```bash
    php artisan serve
    ```

Ahora puedes acceder a tu aplicación Laravel en [http://localhost:8000](http://localhost:8000).

## Documentación de las APIs

- [API RESTful](API-RESTful.md)
- [API GraphQL](API-GraphQL.md)

Cada enlace dirige a un archivo Markdown independiente que contiene documentación detallada sobre cada API implementada en el proyecto. ¡Disfruta explorando las diferentes APIs!

