# CBasicoMongoDB
Curso Básico de MongoDB Curso Básico de MongoDB

## Bases de datos NoSQL
  Las bases de datos NoSQL tienen 4 grandes familias: Key Value Stores, basadas en grafos, columnares y basadas en documentos.

  - Key Value Stores: Guardan la información en formato de llaves y valores. Las usamos para guardar cache, información de sesión de los usuarios o cosas muy sencillas. Son muy rápidas de consultar pero no podemos usarlas en casos más complejos donde necesitamos estructuras más especiales. El mejor ejemplo de estas bases de datos es [Redis](https://redis.io/).

  - Graph Databases: Bases de datos basadas en Grafos. Nos permiten establecer conexiones entre nuestras entidades para realizar consultas de una forma más eficiente que en bases de datos relacionales (así como Twitter o Medium donde cada publicación tiene diferentes relaciones entre sus usuarios, likes, etc). Por ejemplo: Neo4j o JanusGraph.

  - Wide-column Stores: Bases de datos columnares. Tienen una llave de fila y otra de columnas para hacer consultas muy rápidas y guardar grandes cantidades de información pero modelar los datos se puede volver un poco complicado. Las usamos en Big Data, IoT, sistemas de recomendaciones, entre otras. Por ejemplo: Cassandra o HBase.

  - Document Databases: Bases de datos basadas en documentos. Nos permiten guardar documentos dentro de colecciones, tiene muy buena performance y flexibilidad que nos permite modelar casos de la vida real de forma sencilla y efectiva. Por ejemplo: MongoDB o CouchBase.

## Definición de MongoDB y su ecosistema (herramientas de uso)
  MongoDB es una base de datos gratis y de código abierto No Relacional basada en documentos que nos permite guardar una gran cantidad de documentos de forma distribuida. Mongo también es el nombre de la compañía que desarrolla el código de esta base de datos.

  Una de sus principales características es que nos permite guardar nuestras estructuras o documentos en formato JSON (no exactamente JSON, pero si algo muy parecido, lo veremos más adelante) para tener una gran flexibilidad a la hora de modelar situaciones de la vida real.

  Por ser una base de datos distribuida podemos hablar no de uno sino de varios servidores, lo que conocemos como el Cluster de MongoDB. Gracias a esto obtenemos una gran escalabilidad de forma horizontal (escalabilidad en cantidad de servidores).

  MongoDB es “Schema Less” lo que permite que nuestros documentos tengan estructuras diferentes sin afectar su funcionamiento, algo que no podemos hacer con las tablas de las bases de datos relacionales. Su lenguaje para realizar queries, índices y agregaciones es muy expresivo.

## MongoDB Atlas
  MongoDB Atlas es una herramienta de MongoDB que nos permite crear una base de datos en la nube.
  Tenemos varios proveedores que nos permiten utilizar o alquilar MongoDB como servicio y en este caso vamos a usar [MongoDB Atlas](https://www.mongodb.com/atlas/database) por ser desarrollado por las mismas personas que desarrollan MongoDB.

  MongoDB Atlas tiene las siguientes características:

  - Aprovisionamiento automático de clusters con MongoDB
  - Alta disponibilidad
  - Altamente escalable
  - Seguro
  - Disponible en AWS, GCP y Microsoft Azure
  - Fácil monitoreo y optimización

  Creamos nuestro primer cluster en MongoDB Atlas:
  - Nos movemos a [MongoDB](https://www.mongodb.com/)
  - Products -> Atlas -> [Try Free](https://www.mongodb.com/cloud/atlas/register) rellenamos el formulario y nos registramos.
  - Creamos nuestro cluster.

## Instalación MongoDB Mac/Linux o Uso de Docker
  - Ingresa a este [Link](https://www.mongodb.com/try/download/community) y descarga la última versión de MongoDB.
  - Repo para Ubuntu 20.04 .deb[Link](https://repo.mongodb.org/apt/ubuntu/dists/focal/mongodb-org/5.0/multiverse/binary-amd64/mongodb-org-shell_5.0.9_amd64.deb) link de los pasos [instalación](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-20-04-es)
  - Correr MongoDB con un contenerdor de Docker:
    - Corremos el contenedor "docker run --name contenedormongodb -d mongo:lastet" [link](https://hub.docker.com/_/mongo).
    - Ejectuamos "docker exec -it contenedormongodb mongo" para entrar al contenedor.
    - Ya dentro del contenedor hacemos la conexion con el host de nuestra base de datos. "mongosh "mongodb+srv://curso-mongo-platzi.oevehli.mongodb.net/basedatospreviaconfig" --apiVersion 1 --username userprevioconfig" 

## Mongo Shell, configuración de clientes "Conexion desde terminal o forma gráfica"
  Desde la terminal podemos conectarnos a nuestra base de datos con el siguiente comando:
  ``` 
  mongo "mongodb+srv://curso-mongo-platzi.oevehli.mongodb.net" --username jpmjim
  ```
  Y ingresas la contraseña.
  Comandos:
  - `show dbs`: Muestra las bases de datos.
  - `use databse`: Crea una base de datos.
  - Crear una colección:
    ```
    db.inventory.insertOne({ 
      item: "canvas", 
      qty: 100, tags: ["cotton"], 
      size: { 
        h: 28, 
        w: 35.5, 
        uom: "cm" 
        } 
    })
    ```
  - `show collections`: Muestra las colecciones.
  - `db.inventory.findOne()`: Muestra un documento de la colección.

Conexion interfaz grafica 
  - Descargamos el instalador de MongoDBCompass: [Link](https://www.mongodb.com/download-center/compass)
  - En la conexion solamente añadimos la URI
  ```
  mongodb+srv://jpmjim:<password>@curso-mongo-platzi.oevehli.mongodb.net/test
  ```


