# Lambda Function

Instalar las dependencias necesarias

```
npm install
```

En el directorio raiz del proyecto construir una imagen Docker ejecutando el siguiente comando, el archivo Dockerfile ya se encuentra creado y configurado
```
docker build -t filter-products .
```
Asegurate de tener docker instalado para que funcione correctamente.

Posteriormente debes ejecutar el siguiente comando, para inicializar de forma local tu contenedor de Docker
```
docker run -p 9000:8080 filter-products
```
El nombre **filter-products** es para fines del ejemplo, puedes agregarle el nombre que tu quieras a tu contenedor

Una vez este en ejecucion la funcion lambda, debemos verificar el funcionamiento de la misma, podemos usar postman para el ejemplo o por CMD
### Postman
```
POST > http://localhost:9000/2015-03-31/functions/function/invocations
```
en el body de la request debes pasar como parametro un precio
```
{
    "price": 10.000
}
```
Response:
Un listado con el nombre de los productos, que contienen un precio mayor al indicado en el body de la request.
```
{"statusCode":200,"body":["PLAY STATION 3","XBOX ONE","PLAY STATION 5","NINTENTO SWIFT"]}
```
### CMD

Por cmd podemos ejecutar el siguiente comando:
```
curl -XPOST "http://localhost:9000/2015-03-31/functions/function/invocations" -d '{"price": 150}'
```

