## Introducción

A continuación se mostraran los detalles de lo que es la Api de Colores

- [Listado de tecnologías o frameworks utilizados].
- [Cómo instalar las dependencias y correr el proyecto].
- [Documentación].
- [Url de producción].

## Listado de tecnologías o frameworks utilizados

Ésta api esta desarrollada con el lenguaje PHP version 8.0 y el framework de Laravel version 9, se utilizó git para el versionamiento y heroku como servidor. Es muy fácil de utilizar y ya lo verá más adelante.

## Cómo instalar las dependencias y correr el proyecto

A continuación se mostraran los pasos 1 a 1 para poder dejar el proyecto funcionando localmente

- [Clonar el siguiente repositorio](https://github.com/MaironU/pruebaamericas)[con el comando git clone https://github.com/MaironU/pruebaamericas]
- [Luego de clonar entrar a la carpeta por consola usando cd pruebaamericas/].
- [Instalar las dependencias correspondientes con el comando composer install, dado el caso que ocurra un error se va a la raiz del proyecto y crea una carpeta llamada vendor y vuelve a ejecutar el comando.
- [Una vez instalado las dependencias crear un archivo llamado .env en la raiz del proyecto para añadir la configuración correspondiente de la bdd].
- [Una vez creado el archivo .env abrir el archivo .env.example que trae laravel por defecto, copiar toda la información y pegarla en el archivo .env creado anteriormente].
- [Luego crear la bdd, usted escoge el nombre que desee, una vez creada la bdd se va al archivo .env y en DB_DATABASE poner el nombre de la base de datos que creó y en DB_PASSWORD poner la contraseña, en caso de no tener contraseña dejar vacío. Ejemplo: DB_DATABASE=nombrebdd y DB_PASSWORD=].
- [Una vez configurada la bdd, abrir la consola ubicarse en el proyecto y correr el comando php artisan config:cache].
- [Luego ejecutar el siguiente comando php artisan migrate --seed, para crear las tablas y añadir los datos de los colores por defecto].
- [Si llegaste hasta aqui ya debes tener la bdd funcionando correctamente].
- [Luego vas a ejecutar el comando php artisan serve, para levantar el servidor].
- [Y listo ya puedes empezar a usar la Api de Colores].

Importante: recuerda que al momento de ejecutar php artisan ser se te genera una url que es el DOMINIO del proyecto, ese DOMINIO es el que utilizará para hacer las peticiones a la api.

### Documentación

Rutas

- GET DOMINIO/api/colores Este endpoint obtiene todos los colores que hay en la bdd, de manera paginada, 10 datos por página

- GET DOMINIO/api/colores/id Este endpoint obtiene un COLOR en específico recibe como parámetro un id de tipo entero que es el id del color en la bdd EJEMPLO: DOMINIO/api/colores/1 esto retornara: 
{
    "data": {
        "id": 1,
        "name": "cerulean",
        "color": "#98B2D1",
        "year": "2000",
        "pantone_value": "15-4020",
        "created_at": "2022-04-20T16:31:55.000000Z",
        "updated_at": "2022-04-20T16:31:55.000000Z"
    },
    "message": null,
    "response": true,
    "code": 200
}

- POST DOMINIO/api/colores Este endpoint crea un COLOR y recibo como body un objeto como el siguiente: 
{
	"name": "nuevo",
	"color": "#4949dfddddd",
	"year": "2020",
	"pantone_value": "14-4090"
}

todos los parametros son requeridos.

- PUT DOMINIO/api/colores/id Este endpoint actualiza un COLOR en específico,  se debe enviar el id del COLOR a actualizar y como body un objeto con los datos a actualizar, Ejemplo:

{
	"name": "Nuevo nombre",
}

En este caso estoy enviando por body este objeto que significa que solo quiero actualizar el nombre del Color, si deseo actualizar otro dato, podria enviarlo tambien desde el mismo objeto.

- DELETE DOMINIO/api/colores/id Este endpoint elimina un COLOR y recibo como parámetro el id del color que se quiere eliminar.


Importante: Todas las rutas al final de cada url puede recibir un parametro que es opcional que se llama xml.

Ejemplo: DOMINIO/api/colores?xml=1 al enviar xml=1 la api retornara los datos en xml si se envia 0 que es por defecto los retornada como un json.

Tambien tener en cuenta la estructura del objeto recibido:

{
    "data": {  // Este campo es el que muestra la información real de los colores
        "id": 1,
        "name": "cerulean",
        "color": "#98B2D1",
        "year": "2000",
        "pantone_value": "15-4020",
        "created_at": "2022-04-20T16:31:55.000000Z",
        "updated_at": "2022-04-20T16:31:55.000000Z"
    },
    "message": null, // Este es el mensaje de la respuesta
    "response": true, // Este es el status si fue correcto es true si hubo un error es false
    "code": 200 // y este es el codigo http de la respuesta
}


### Documentación

La Api ha sido subida a un servidor de heroku la url es la siguiente:
https://apicolores.herokuapp.com

Puede probar la api tanto en local como en producción sin ningún problema

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
