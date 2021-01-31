# Generador Datos Desafio Fork

Este proyecto expone un API REST que entrega la siguiente información:

_id_: identificador
_fechaCreacion_: Fecha de inicio de la secuencia
_fechaFin_: Fecha de fin de la secuencia
_fechas_: Lista de fechas que están en el rango de la fecha que se encuentra en “fechaCreacion” hasta la fecha “fechaFin”
Ejemplo.

```json
{
  "id": 6,
  "fechaCreacion": "1968-08-01",
  "fechaFin": "1971-06-01",
  "fechas": ["1969-03-01", "1969-05-01", "1969-09-01", "1971-05-01"]
}
```

_Nota_:
El formato de las fechas es yyyy-MM-dd
El servicio entrega 1 periodos, el periodo contiene una fecha inicial una fecha final y una lista fechas.

# Detalle de los sistemas

Swagger Codegen 2.3.1 (OpenApi 2.0)
Java 8
Spring-Boot 1.5.11.RELEASE
Maven 3

# Compilar y ejecutar el proyecto

Para copilar el proyecto se requiere Java y Maven instalado.
Ingresar al directorio _ApiPeriodos_ ejecutar el siguiente comando _maven_

```bash
mvn package
```

Luego de compilar el proyecto ingresar al directorio _target_ ejecutar el siguiente comando _java_

```bash
java -jar .\api-periodos-1.0.0.jar
```

_Nota_:
Debe estar disponible el puerto _8080_ en el PC donde se ejecute esta API

# Visualizar Documentación y consumir la API

La documentación swagger del API (una vez que se levanta el API) queda disponible en

http://127.0.0.1:8080/periodos/swagger-ui.html#/

Para consumir el servicio se debe invocar la siguiente URL

```bash
curl -X GET --header 'Accept: application/json' 'http://127.0.0.1:8080/periodos/api'
```

# Regenerar API a partir de yaml

Las siguientes instrucciones solo son para re-escribir el API si es necesario agregar una nueva funcionalidad a partir del _YAML_.

Bajar SwaggerCodeGen 2.3.1 en la raíz del proyecto, ejecutando el siguiente comando por consola.

```bash
wget http://oss.sonatype.org/content/repositories/releases/io/swagger/swagger-codegen-cli/2.3.1/swagger-codegen-cli-2.3.1.jar -O swagger-codegen-cli.jar
```

Para re-crear el código a partir de la definición del _YAML_ de swagger ejecutar el siguiente comando

```bash
java -jar .\swagger-codegen-cli.jar generate -i .\swagger\periodos.yaml -l spring -c .\swagger\config.json -o ApiPeriodos --ignore-file-override .\.swagger-codegen-ignore
```

_Nota_:
Esto creara toda la estructura de swagger y re-escribirá todas las clases que no estén declaradas en el archivo _.swagger-codegen-ignore_
