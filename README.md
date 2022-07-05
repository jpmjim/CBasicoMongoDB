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
## MongoDB + Drivers
  [Drivers](https://www.mongodb.com/docs/drivers/drivers/)
  ¿Qué son los drivers en MongoDB?
  Son las librerías que utilizamos para comunicar nuestra aplicación con nuestra base de datos.
  Sin nuestros drivers no podemos trabajar con nuestros cluster de base de datos.
  📝
  ¿Cómo agregar los drivers dentro de nuestro proyecto?
  Usamos un gestor de dependencias. Lo agregamos en nuestro gestor de dependencia; si usamos NodeJS, utilizamos ‘npm install mongodb --save’.

  Instalación de los drivers de MongoDB en diferentes lenguajes:
  - NodeJS: npm install mongodb
  - Python: pip install pymongo
  - Java: mvn install:install-file -Dfile=<path-to-driver> -DgroupId=com.mongodb.driver -DartifactId=mongodb-driver -Dversion=<version> -Dpackaging=jar
  - C#: NuGet install MongoDB.Driver
  - Go: go get github.com/mongodb/mongo-go-driver/mongo
  - Ruby: gem install mongo
  - PHP: composer require mongodb/mongodb
  - Elixir: mix deps.add mongodb
  - Swift: pod install mongodb
  - Kotlin: addRepository "MongoDB"

## Bases de datos, Colecciones y Documentos en MongoDB
  Las Bases de Datos son los contenedores físicos para nuestras colecciones. Cada base de datos tiene un archivo propio en el sistema de archivos de nuestra computadora o servidor y un Cluster puede tener múltiples bases de datos.

  Las Colecciones son agrupaciones de documentos. Son equivalentes a las tablas en bases de datos relacionales pero NO nos imponen un esquema o estructura rígida para guardar información.

  Los Documentos son registros dentro de las colecciones. Son la unidad básica de MongoDB y son análogos a los objetos JSON pero en realidad son BSON.

  ![](http://4.bp.blogspot.com/-edz2_QrFvCE/UnzBhKZE3FI/AAAAAAAAAEs/bTEsqnZFTXw/s400/SQL-MongoDB+Correspondence.PNG)

  [JSON and BSON](https://www.mongodb.com/json-and-bson)

  - JSON: Es una representación textual de un objeto.
  - BSON: Es una representación binaria de un objeto.

  BSON está diseñado para ser eficiente en el espacio, pero en algunos casos no es mucho más eficiente que JSON. En algunos casos, BSON usa incluso más espacio que JSON. La razón de esto es otro de los objetivos de diseño de BSON: la capacidad de desplazamiento. BSON agrega información “adicional” a los documentos, como la longitud de cadenas y subobjetos. Esto hace que el recorrido sea más rápido.

  BSON también está diseñado para ser rápido de codificar y decodificar. Por ejemplo, los enteros se almacenan como enteros de 32 (o 64) bits, por lo que no necesitan ser analizados desde y hacia el texto. Esto utiliza más espacio que JSON para los enteros pequeños, pero es mucho más rápido de analizar.

  Además de la compacidad, BSON agrega tipos de datos adicionales no disponibles en JSON, especialmente los tipos de datos BinData y Date.

## Operaciones CRUD desde la consola de MongoDB
  Comandos: [Instrucciones y Comandos CRUD](https://static.platzi.com/media/public/uploads/crud_0540220d-88e9-447c-9e03-681375363137.txt)
  - Conexión con el cluster de MongoDB Atlas `mongo "URL DE NUESTRO CLUSTER"` , (recuerda añadir tu IP a la lista de IPs permitidas para no tener problemas en esta parte).
  Listar las bases de datos de nuestro cluster: show dbs.

  - Seleccionar una base de datos: `use NOMBRE_BD`. Debemos crear por lo menos un documento si la base de datos es nueva porque MongoDB no crea bases de datos vacías.

  - Recordar qué base de datos estamos usando: `db`.

  - Listar las colecciones de nuestra base de datos: `show collections`.

  - Crear una colección (opcional) y añadir un elemento en formato JSON: `db.NOMBRE_COLECCIÓN.insertOne({ ... })`. La base de datos responde `true` si la operación fue exitosa y crea el campo irrepetible de `_id` si nosotros no lo especificamos.

  - Crear una colección (opcional) y añadir algunos elementos en formato JSON: `db.NOMBRE_COLECCIÓN.insertMany([{ ... }, { ... }])`. Recibe un array de elementos y devuelve todos los IDs de los elementos que se crearon correctamente.

  - Encontrar elementos en una colección: `db.NOMBRE_COLECCIÓN.find()` Podemos aplicar filtros si queremos o encontrar solo el primer resultado con el método `findOne()`.

  - Listar todos los posibles comandos que podemos ejecutar: `db.NOMBRE_COLECCIÓN.help()`.

  ![](https://static.platzi.com/media/user_upload/Captura-2d4be618-302d-42b6-ab32-8723a04643a6.jpg)
  ![](https://static.platzi.com/media/user_upload/Captura2-fc030661-4be4-4d0e-ac2a-c751a27d2aa2.jpg)

## Operaciones CRUD desde Compass
  Applicaciones mejorar el uso de Mongo DB
  - [MongoDB Compass](https://www.mongodb.com/compass)
  - Para Visual Code [MongoDB for VS Code](https://marketplace.visualstudio.com/items?itemName=mongodb.mongodb-vscode)
  - [Navicat](https://www.navicat.com/en/products/navicat-for-mongodb) 

## Tipos de datos
  [Documentación de tipos de datos](https://docs.mongodb.com/manual/reference/bson-types/)
  - Strings: Nos sirven para guardar textos.
  - Boolean: Información cierta o falsa (true y false).
  - ObjectId: Utilizan el tiempo exacto en el que generamos la consulta para siempre generan IDs únicos. Existen en BSON pero no en JSON.
  - Date: Nos sirven para guardar fechas y hacer operaciones de rangos entre ellas.
  Números: Doubles, Integers, Integers 64 bits y Decimals.
  - Documentos Embebidos: Documentos dentro de otros documentos ({}).
  - Arrays: Arreglos o listas de cualquier otro tipo de datos, incluso, de otras listas.
  ```
  String: `"hola"`
  Number: `1`
  Boolean: `true` o `false`
  Null: `null`
  Object: `{}`
  Array: `[]`
  Binary: `new Buffer("hola")`
  Date: `new Date()`
  Timestamp: `new Timestamp()`
  RegExp: `/^hola/`
  JavaScript: `function() {}`
  JavaScriptWithScope: `{ $scope: { ... } }`
  Int32: `new Int32()`
  Timestamp: `new Timestamp()`
  Int64: `new Int64()`
  Decimal128: `new Decimal128()`
  MinKey: `new MinKey()`
  MaxKey: `new MaxKey()`
  ```

## ¿Qué son los esquemas y las relaciones?
  Los esquemas son la forma en que organizamos nuestros documentos en nuestras colecciones. MongoDB no impone ningún esquema pero podemos seguir buenas prácticas y estructurar nuestros documentos de forma parecida (no igual) para aprovechar la flexibilidad y escalabilidad de la base de datos sin aumentar la complejidad de nuestras aplicaciones.

  Las relaciones son la forma en que nuestras entidades o documentos sen encuentran enlazados unos con otros. Por ejemplo: Una carrera tiene multiples cursos y cada curso tiene multiples clases.

  ### MongoDB 🆚 SQL: [MongoDB vs SQL](https://platzi.com/blog/mongo-vs-sql/)

  - 💃 MongoDB tiene mucha flexibilidad y no nos impone seguir una estructura o esquema bien definido.
  - 🙅 SQL nos impone una estructura bien definida a más no poder; es super no-flexible.
  - 🍻 Con MongoDB es más fácil empezar y añadir nuevas funcionalidades.
  - ⏲ Con SQL es más demorado de empezar porque debemos tener el orden super claro siempre. Todos los elementos deben tener los mismos elementos y todos deben ser del mismo tipo. Si queremos agregar un nuevo campo debemos añadirlo en todas partes con un valor pode defecto, aunque no lo necesitemos.
  - 🤒 Si no seguimos buenas prácticas en MongoDB, vamos a necesitar queries ultra-complejas, demoradas y una visita diaria al psicólogo 😱.
  - 💆 El orden impuesto de SQL no es por nada. Las queries son fáciles de entender porque todo sigue su orden y tranquilidad. Aunque, implementar nuevas features toma su buen tiempo 🤔.
