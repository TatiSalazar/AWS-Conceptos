# Introducción a AWS : Cómputo, Almacenamiento y bases de datos

# AWS EC2
* Permite alquilar computadoras virtuales.
* Diferentes tipos de EC2 con diferente CPU (para alto rendimiento), RAM y almacenamiento (para grandes cargas de trabajo).
* Instancias optimizadas en computación (para leer y escribir muy rápido)
* El sistema de pago más común: paga por hora o segundo, dependiendo el tipo de instancia

**Ejemplos precios**
$0.1 la hora
24 * 0.10 = $2.40
Pagas lo mismo por
* 24 tareas de 1h en una instancia
* 24 instancias de 1h

***Elastica** significa que la instancia es redimensionable

## Opciones y precios bajo demanda

Las instancias pueden redimiensionarse. Puedes empezar por una instancia de bajo costo, y si necesitas aumenta su capacidad, apagas la instancia y seleccionas un nuevo tipo de instancia. Cuando enciendas de nuevo la instancia, verás su capacidad aumentada. La siguiente tabla muestra algunos tipos de instancias.

* Nombre de la instancia: t3.nano (baja potencia)
   * Especificaciones: 2 vCPU’s, 0.5 GiB RAM
   * Precio: $0.0052/hour

* Nombre de la instancia: t3.xlarge
   * Especificaciones: 4 vCPU’s, 16 GiB RAM
   * Precio: $0.1664/hour

* Nombre de la instancia: c6g.8xlarge
   * Especificaciones: 32 vCPU’s, 64 GiB RAM
   * Precio: $1.088/hour

* Nombre de la instancia: X1e.xlarge
   * Especificaciones: 128 vCPU’s, 3904 GiB RAM, 2x 1920 GB SSD
   * Precio: $26.688/hour

## On Demand
* Las instancias bajo demanda son ideales para cargas de trabajo irregulares a corto plazo que no se pueden interrumpir. 
* No se aplican costos iniciales ni contratos mínimos. 
* Las instancias se ejecutan de forma continua hasta que las detengas y solo pagas por el tiempo de cómputo que utilizas.

## Contenedor
El propósito de un contenedor es **crear un paquete de tu programa y todas sus librerías y dependencias con las versiones específicas con las que has trabajado, para producir una imagen que pueda ser ejecutada en cualquier máquina.**

Un problema común del desarrollo de software es utilizar distintas versiones de diferentes librerías/lenguajes de programación/programas. **Docker nos permite crear contenedores para resolver este problema.**

**Los alojamientos (host dedicados) dedicados de Amazon EC2** le permiten utilizar licencias de software elegibles de proveedores como Microsoft y Oracle en Amazon EC2 para obtener la flexibilidad y rentabilidad de utilizar sus propias licencias, pero con la resiliencia, simplicidad y elasticidad de AWS. Un alojamiento dedicado de Amazon EC2 es un servidor físico dedicado completamente para su uso personal, por tanto usted puede ayudar a abordar los requisitos de conformidad corporativos.

El alojamiento dedicado de Amazon EC2 también está integrado con AWS License Manager, un servicio que le ayuda a administrar sus licencias de software, incluidas las licencias de Microsoft Windows Server y Microsoft SQL Server. Con License Manager puede definir los términos de sus licencias para controlar el uso de las licencias, como también definir sus preferencias de administración de alojamientos dedicados para la asignación de alojamientos y uso de capacidad de alojamiento. Luego de configurarlo, AWS realiza estas tareas administrativas por usted para que pueda lanzar máquinas virtuales (instancias) de manera continua en alojamientos dedicados de la misma manera en que lanzaría una instancia EC2 con licencias proporcionadas por AWS.

## Amazon ECS (Elastic Container Service)
Amazon ECS es un servicio de contenedores, donde puedes implementar tus imágenes en contenedores en AWS. Cuando corras tus contenedores en AWS, no notarás diferencia entre tu máquina local y el entorno de AWS.

## AWS LAMDDA
Es un servicio serverless que nos permite ejecutar código en respuesta a eventos, sin preocuparnos por servidores o infraestructura. Estos eventos pueden ser temporizadores, visitas a alguna sección de nuestra aplicación, solicitudes HTTP, entre otros.

* Supongamos que queremos tener una aplicación que diariamente envia un mensaje en twitter
* Requisitos
  * API twitter, EC2, SO Linux, lenguaje de programación python
  * Network, hard drive, actualizaciones
* AWS Lambda
  * Servicio informático sin servidor
  * Ejecuta su codigo en respuesta a eventos
 * Caso de uso
  * Subes una imagen y el lambda crea varias resoluciones
 
 * Facturación por milisegundos
  * El precio depende del uso de RAM
  * 128 MB Ram x 30 M eventos por mes
  * $11.63 al mes 
  
  ## Tipos de almacenamiento
  
  * **Archivo (sistema de ficheros)** en carpeta en nuestro ordenador
      * Amazon Elastic File System (EFS) 
      * Amazon FSx for Window File Server
  * **Bloque** los archivos se almacena en volúmenes por fragmentos de datos de igual tamaño, sin procesar
      * Amazon Elastic Block Store (EBS)
      * Bases de datos, servidor de correo electrónico 
  *  **Objeto**  la información almacenada recibe un identificador único y se almacenan en un sistema de memoria plana
      * Amazon Simple Storage Service (S3)

##  Respaldo
  * Amazon Backup
  
## Transferencia de datos
  * **AWS Storage Gateway** Es un conjunto de servicios de almacenamiento en la nube híbrida que le brinda acceso en las instalaciones al almacenamiento en la nube prácticamente ilimitado
  
  * **AWS DataSync** Es un servicio seguro en línea que automatiza y acelera el traslado de datos entre las instalaciones y los servicios de almacenamiento de aws.
  
  * **AWS Transfer Family** Escala de forma segura sus transferencias recurrentes de archivos de empresa a empresa a *Amazon S3 y Amazon EFS con los protocolos SFTP, FTPS y FTP*

## S3
Es un servicio de almacenamiento de objetos, líder en la industria. Otorga una garantía de no pérdida de datos del 99.999999999% (11 9’s).

* **S3 Standard** almacenamiento de objetos de alta durabilidad, disponibilidad y rendimiento para datos a los que se obtiene acceso con frecuencia.

* **S3 Standard-IA** se utiliza con datos a los que se accede con menos frecuencia, pero que requieren un acceso rápido cuando es necesario

* **S3 Zone-IA** similar a Standard-IA, pero con un menor costo de almacenamiento ya que solo usa una zona de disponibilidad. Distinto de las demás clases de almacenamiento de S3, que almacenan datos en un mínimo de tres zonas de disponibilidad (AZ)

* **S3 Glacier** ofrece el almacenamiento de menor costo para los datos de larga duración y acceso poco frecuente. Tiene un costo de $1 por TB al mes. Tiene tres opciones para la recuperación de datos (estándar, masica y acelerada)

* **S3 Glacier Deep Archive** la clase de almacenamiento más económica de Amazon S3. Admite la retención a largo plazo y la conservacipon digital de datos a los que se accede una o dos veces al año.

* **S3 Intelligent-Tiering** un tipo de almacenamiento que intenta ahorrar costos moviendo archivos entre los distintos tipos de almacenamiento S3, basado en los patrones de uso de los archivos.
  
* **S3 Standard** si necesitamos un almacenamiento altamente disponible y duradero, usamos **S3 Glacier**  si necesitamos a largo plazo y de acceso infrecuente

## Amazon Elastic System (EFS) 
Brinda un sistema de archivos elástico, sencillo, sin servidor y práctico basado en NFS para las máquinas virtuales de EC2
* Altamente disponible y duradero
* Provee protección contra una interrupción de la zona de disponibilidad, replicando los archivos en múltiples zonas dentro de una región 

* brinda dos clases de almacenamiento
    * Standar y Standar IA (para acceso poco frecuente). Puedes implementar políticas para que tus archivos se muevan de Standar IA después de cierto tiempo
    * Los datos están **encriptados de manera automática**

## NFS
* Es un protocolo de archivos en red que permite acceder a archivos y directorios que no están en tu sistema. Esto permite que miles de máquinas puedan conectarse a EFS y procesar los datos que allí se encuentran.

## AWS Storage Gateway
* Nos brinda acceso a almacenamiento en la nube prácticamente ilimitado desde nuestra propia infraestructura
* Se compone de 3 puertas de acceso : 
    * **File Gateway** 
    * Provee interfaces SMB y NFS para amazon S3, tanto en Windows como en linux. Los cuales escriben archivos al sistema y File Gateway se encarga de guardarlos en S3. Los archivos S3 pueden ser usados por cualquier servicio AWS.
    * **Tape Gateway**
    * Permite migrar copias de seguridad a una bilbioteca de cintas virtuales en AWS. Se guardan en S3 y se puede implementar S3 Glacier y S3 Glacier Deep Archive para guardar tus copias de seguridad a largo plazo.
    * **Volume Gateway**
    * Otorga almacenamiento en bloque con protocolo iSCSI, respaldado en la nube. Almacena datos en S3 de acuerdo 2 modos:
    * *Modo caché* los datos principales se almacenan en S3, y, los datos de acceso frecuente se guardan localmente y en caché
    * *Modo almacenado* todos los datos se guardan localmente, mientras se hacen una copia de seguridad de manera asincrona en S3

**Versionamiento S3**
* Cada vez que subimos un archivo con el mismo nombre a un bucket con versionamiento habilitado, se crea una nueva version del mismo, y se le asigna un ID único de objeto. Las versiones anteriores de los archivos también se almacenan, lo que puede suponer un mayor costo.

## Bases de datos relacionales
  * **Amazon Aurora** compatible con MYSQL y PostgresSQL creada para la nube
  * **Amazon Redshift** ideal para analítica. Usa SQL para analizar datos estructurados en almacenamientos de datos, con hardware y machine learning diseñados por aws. 

## Bases de datos clave-valor
  * **Amazon DynamoDB** es una base de datos de documentos y valores clave que ofrece un rendimiento de milisegundos de un solo digito a cualquier escala.
  * Para aplicaciones de web de alto tráfico, sistema de comercio electrónico y aplicaciones de juego

## Bases de datos en memoria
* **Amazon ElastiCache** es un servicio de almacenamiento de caché en memoria 
* En casos de uso flexibles y en tiempo real
* Para memcached y redis
* Acelera el rendimiento de las aplicaciones: accede a los datos con latencia de microsegundos y un alto rendimiento para que las aplicaciones funcionen rápido
* Reduce la carga de la bd del backend
* Cree almacenes de datos de baja latencia
* Caso de uso: Sitio de noticias: Acelera la velocidad con la que se encuentran los articulos en la bd, en lugar de acceder a la bd cada vez que llegue un visitante, los articulos ya estan listos para ser enviados por la memoria caché
* Empresas que lo usan: Peloton, AirBNB, Duolingo

## Bases de datos basadas en documentos
* **Amazon DocumentDB** es un servicio de base de datos de larga duración
* Alta disponibilidad, rápida, escalable y completamente administrado para operar cargas de trabajo de MongoDB

## Amazon RDS
* permite crear, ejecutar bases de datos relacionales en la nube
* se consulta a traves de sql
* MYSQL, MariaDB, PostgreSQL, Oracle, SQL Server y Amazon Aurora
* Administrado por PAAS
* Altamente escalable, multiples zonas de disponibiliad
* Permite crear réplicas de bases de datos de solo lectura
* Realiza copias de seguridad automática y es tolerante a fallos
* Solo pagas por lo que usas

## DynamoDB
* Es una base de datos NOSQL de documentos de clave-valor
* Rendimiento en milisegundo de un solo dígito
* Manejo de datos actualizados en tiempo real
* Administrado por PAAS
* Seguridad, respaldo y restauración integrados
* Adminite picos de 20,000,000 de solicitudes por segundo
* Rentable
* Casos de uso: Publicidad, juegos, ecommerce, bancos, redes sociales, media entertainment, propio internet

