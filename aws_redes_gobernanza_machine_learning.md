# Introducción a AWS Redes, Gobernanza y Machine Learning

## VPC (Virtual Private Cloud)

* RED VIRTUAL PRIVADA
* Cada computadora que está conectada a otra computadora por medio de un cable, enrutador o antena de wifi, requiere de una interfaz de red para ser conectada.
*  La interfaz de red es el puente entre nuestra computadora y la tecnología ya utilizada para conectarse a la otra computadora.
*  Una vez que conectamos las computadoras, debemos configurar la red, para lo cual necesitamos un rango de direcciones IP.

* Permite lanzar recursos de AWS en una red virtual en la nube de amazon
* Puede controlar todos los aspectos del entorno de redes virtual
* Incluida la selección de sus propios rangos de direcciones IP
* La creación de subredes y la configuración de tablas de ruteo y gateways de red
* Crear VPN de hardware entre el centro de datos de la empresa y la vpc, y utilizar la nube de aws como una prolongacion del centro de datos corporativo

## Rango direcciones IP
* El rango de direcciones IP es como una comunidad cerrada local, donde los equipos se podrán comunicar solo con otros equipos dentro de la misma red.
* se le dan 4 números que varían del 0 al 255 separados por un punto.
* Para redes privadas ya se tienen especificados los rangos de IP:
* 10.0.0.1
* 172.16.0.1
* 192.168.0.1

## COMPONENTES AMAZON VPC
* Amazon VPC permite crear una red virtual para poder conectarnos a todos los servicios de AWS que existan en un rango de direcciones IP locales (por ejemplo, 10.0.0.0/24, que representa del rango de IP entre 10.0.0.0 y 10.0.0.255).
* Esta red virtual será como una pequeña comunidad cerrada para nuestras máquinas virtuales y todos los servicios que tengamos dentro de AWS.
* componentes:
* **Nat Gateway** si deseamos que nuestras máquinas virtuales puedan acceder a internet, debemos utilizar este componente
* **Internet Gateway** permite que internet pueda acceder a nuestra instancia de EC2
* **ACL Control List** controla el trafico que vamos a permitir dentro y fuera de la vpc

* **Nube virtual privada** una red virtual aislada de forma 


## Redes
* Son cómo están conectadas las computadoras (y otros dispositivos tecnológicos) entre sí, y los servicios que permiten esto.
* Para que Internet funcione es necesario contar con direcciones IP, enrutadores, DNS y seguridad.
* AWS provee servicios que permiten la creación de redes y la entrega de contenido a los usuarios de manera rápida.

## Redes en la nube
* **Amazon Virtual Private Cloud** permite definir y aprovisionar una red privada para nuestros recursos de AWS
* **AWS Transit Gateway** Permite conectar VPC con los recursos locales (on-premises) mediante un hub central
* **AWS PrivateLink**  proporciona conectividad privada entre las VPC y aplicaciones locales, sin exponer el tráfico al Internet público
* **Amazon Route 53** permite alojar nuestro propio DNS administrado

## Redes a escala
* Estos servicios nos permiten escalar el tráfico de red según las necesidades:
* **Elastic Load Balancing** permite distribuir automáticamente el tráfico de red a través de un grupo de recursos, con el fin de mejorar la escalabilidad
* **AWS Global Accelerator:** redirige el tráfico a través de la red global de AWS para mejorar el rendimiento de las aplicaciones globales
* **Amazon CloudFront** entrega de forma segura datos, videos y aplicaciones a clientes de todo el mundo con baja latencia.

## CLOUDFRONT
* Es un servicio intermedio entre el navegador (o el cliente) y el sitio web
* **El propósito  es entregar datos, aplicaciones y sitios web en todos el mundo con baja latencia.**
* Cuenta con Edge Locations (ubicaciones de borde) multiples ubicaciones en el mundo
* Guarda en cache por un tiempo en especifico
* Cualquier cambio que realicemos en los archivos se replicará en las ubicaciones de borde a medida que sus visitantes están entrando y solicitando el contenido
* **Caracteristicas : *
  * Seguro: proteccion contra ataques DDOS, protegido contra los picos de trafico
  * También permite ejecutar funciones de AWS Lambda en las ubicaciones de borde
  * CloudFront ofrece múltiples métricas en tiempo real, y es rentable.

**Amazon CloudFront es un servicio de red de entrega de contenido (CDN) creado para ofrecer un alto rendimiento, seguridad y facilita la entrega de sitios web, videos, aplicaciones y API de forma segura a altas velocidades con baja latencia.**
Entonces que es un CDN? es una Red de Distribución de Contenido, por sus siglas en ingles Content Delivery Network, es un sistema de servidores distribuidos en una red que despliegan contenido de tipo estático

## Route 53
* DNS es un sistema que asigna direcciones IP a nombres de dominio
* Route 53 es un servicio de alojamiento de DNS
* Cuesta $0.5 por nombre de dominio por mes.
* Es un servicio complejo pero es util para mantener nuestros sitios web rapidos y altamente disponible.
* Es rentable, seguro, escalable, y posee opciones de enrutamiento para distintos casos.
* **Politicas de enrutamiento**
  * **Ruteo simple** utilice el servicio de DNS estándar. El trafico en un dominio se enruta hacia un recurso muy especifico
  * **Politica ponderada** (weighted routing) permite asociar multiples recursos con un solo nombre de dominio y ver que tanto trafico es dirigido a cada recurso. Esto se determina con un número del 0 al 255, **donde el cero representa que el recurso no recibe ningún tráfico, y el 255 indica que el recurso recibe todo el tráfico**.
  * **Politica geolocalizacion** se pueden escoger que recursos servir en funcion de la ubicacion geografica de nuestros usuarios. Esto permite servir contenido especifico segun la region, tambien, restringir la distribucion del mismo solo a las regiones permitidas.
  * **Politica de latencia** entregar los recursos desde la región de AWS que esté más cercana a la ubicación del usuario, a fin de reducir el tiempo de respuesta.
  * **Política de conmutación por error** redirige el trafico a un recurso cuando este esta en buen estado, o a uno diferente cuando el primer recurso no esta en buen estado
  * **Politica de respuesta de multiples valores** permite devolver varios valores, como direcciones IP  a los servidores web, en respuesta a las consultas de DNS.
  
  ## Administracion y gobernanza
  
 **Administracion de cuentas**
 * **AWS Control Tower** Una forma facil de configurar y gobernar un entorno seguro de AWS de multiples cuentas
 * **AWS Organizations** Una forma de gobernar, administrar centralizadamente los entornos en varias cuentas de aws
 * **AWS Budgets** ayuda a planificar y realizar control de costos

**Servicio de aprovisamiento**
* **AWS CloudFormation** permite modelar y aprovisionar todos sus recursos mediante codigo
* **AWS OpsWorks** ayuda a automatizar todas las operaciones con CHEF y Puppet
* **AWS Service Catalog** Un servicio para crear, organizar y gobernar nuestro propio catalogo de productos de aws
* **Marketplace** es donde vamos a poder encontrar, probar e implementar software que se ejecuta en AWS

**Servicios para operar el entorno AWS**
* **Amazon CloudWatch** permite observar nuestros servicios a traves de metricas y registros
* **Amazon Config** permite registrar y evaluar las configuraciones de nuestos recursos en AWS
* **AWS CloudTrail** rastrea toda la actividad del usuario de la cuenta aws.
* **Systems Manager** optimiza el rendimiento y la seguridad mientras administramos una gran cantidad de sistemas
* **Amazon X-Ray** analiza y depura aplicaciones en produccion

## CloudFormation (infraestructura como código)
* Es un servicio que permite provisionar servicios como máquinas virtuales o VPCs mediante código. 
* Para esto se usan las CloudFormation Templates, que son plantillas en donde especificamos los recursos que queremos desplegar. 
* Estas plantillas pueden estar en formato JSON o YAML, y en ellas se define un stack o pila de recursos a provisionar.
* A esta estructura se le llama pila

```json
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "this template does XXXX",
  "Metadata": {},
  "Parameters": {},
  "Mappings": {},
  "Conditions": {},
  "Transform": {},
  "Resources": {},
  "Outputs": {}
```

* **AWSTemplateFormatVersion**: este parámetro es opcional. Aquí especificamos la versión de la plantilla
* **Description**: cadena de texto que describe la plantilla. Debe ir después de AWSTemplateFormatVersion
* **Metadata**: objetos que proporcionan información adicional sobre la plantilla
* **Parameters**: valores que pasaremos a la plantilla al ejecutarse, ya sea durante la creación o actualización del *stack
* **Mappings**: permite asignar un conjunto de valores a una clave específica. Por ejemplo, para establecer valores en función de una región, podemos crear un mapping que usa el nombre de una región como clave y contiene los valores que deseemos especificar para cada región
* **Conditions**: controla que se creen recursos o se asignen valores a dichos recursos en función de una condición. Por ejemplo, podemos asignar valores distintos para entornos de producción o de prueba
* **Transform**: especifica las macros que AWS CloudFormation usa para procesar la plantilla
* **Resources**: aquí se declaran los recursos a incluir en el stack. Por ejemplo, instancias EC2 o buckets de S3.
* **Outputs**: declara valores de salida que pueden ser usados en otros stacks

* Pasos para crear el stack
* 1. Nos dirigimos a la página de CloudFormation desde nuestra cuenta de AWS (en esta página podremos conocer más sobre el servicio en cuestión).
* 2. Aquí le damos a “Crear stack”.
* 3. Para crear el stack, en “Especificar plantilla” seleccionamos “Cargar un archivo de plantilla”, y cargamos el archivo createstack.json. Este archivo simplemente define un bucket de S3 llamado “platzilab”.
* 4. Le damos clic a siguiente y, a continuación, escogemos un nombre para el stack o pila. En este caso, la llamamos cfnlab, y le damos a siguiente.
* 5. Opcionalmente, podemos añadir etiquetas para identificar la pila, y un rol de IAM.
* 6. Dejamos el resto de configuraciones por defecto y le damos a siguiente. Entonces nos llevará a revisar las configuraciones, y le damos a “Crear pila”.
* 7. Podremos ver el proceso de creación de la pila, los eventos y los recursos que fueron creados. Si te fijas en el nombre del bucket creado, verás que este está compuesto por el nombre de la pila, el nombre que le asignamos al bucket en la plantilla, y una cadena de texto aleatoria. Esto es para evitar crear recursos con nombre duplicados.

* Actualizar pila
* 1. Para actualizar la pila primero usaremos el archivo updatestack1.json. El contenido de este archivo es el siguiente:
```json
{
  "Resources": {
    "platzilab": {
      "Type": "AWS::S3::Bucket"
    },
    "platzilabalexis": {
      "Type": "AWS::S3::Bucket"
    }
  }
}
```

* 2. Ahora, en la página de CloudFormation, escogemos la pila que creamos y le damos a “Actualizar”.
* 3. En “Preparar la plantilla” escogemos “Reemplazar la plantilla actual” y cargamos el archivo updatestack1.json.
* 4. Le damos a Siguiente tres veces, y notamos que en “Vista previa del conjunto de cambios” nos muestra que solo va a añadir un nuevo bucket de S3, puesto que el bucket con ID lógico “platzilab” ya existe. Entonces le damos a “Actualizar pila”.
* Crear pila: Podemos crear otra pila dándole un nombre explícito a los buckets que queremos provisionar. Para ello, usemos el archivo updatestack2.json.
```json
{
  "Resources": {
    "platzilab": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "BucketName": "mibucket123"
      }
    },
    "platzilabalexis  ": {
      "Type": "AWS::S3::Bucket"
    }
  }
}
```
* En este caso el bucket con ID lógico “platzilab” tiene en sus propiedades el nombre de bucket “mibucket123”. Este nombre debe ser único en todo AWS. Si intentamos crear la pila con un bucket con nombre repetido, tendremos un error y no se creará la pila.
Curso de Introducción a AWS: Redes, Gobernanza y Machine Learning cap 13-14 video

## Beneficios CLOUDFORMATION
* **Control de versiones** este codigo se puede guardar en github, para tener un historial 
* **Automatizacion** permite a los encargados de DevOps automatizar la creacion de infraestructura y recursos en aws
* **Escala** Gracias a las plantillas podemos replicar la infraestructura en distintas cuentas de aws y en distintas regiones. Solo se debe ajustar ciertos parametros.

## CloudWatch (Monitorear)
* Es un servicio de supervision y observabilidad para AWS
* Podemos ver todo lo que sucede dentro de nuestra cuenta de AWS
* Recopilar métricas o datos de sus servicios
* Integrar con unos 80 servicios de AWS
* Tener métricas predefinidas
* Recopilar y desplegar datos en una vista unificada con distintos gráficos.
* Configurar de alarmas de acuerdo a los graficos que nos muestre cloudWaatch
* Enviar archivos de registro y buscar de forma interactiva datos de registros

## AutoScaling
* permite escalar la capacidad de nuestras instancias de máquinas virtuales automáticamente
* Podemos aumentar la cantidad de instancias que tenemos en ejecución durante los picos de demanda y disminuirlos cuando no los necesitemos.
* **alta disponibilidad, tolerancia a fallos y un ahorro de costos.**
* Para aprovechar el autoescalamiento, debemos crear un grupo de auto escalamiento que asocie nuestras instancias
* En este grupo especificaremos un tamaño mínimo (el número mínimo de instancias a correr), y una capacidad deseada (el número óptimo de instancias en función de las necesidades).
* **Load Balancer de AWS es lo que permite distribuir automaticamente las conexiones a medida que aparecen y desaparecen estos servidores.**
* **EC2 no es el único servicio que tiene auto escalamiento. DynamoDB y Aurora también implementan este concepto.**

## Machine learning
* Es un tipo de inteligencia artificial donde podemos escribir programas que aprenden de los datos que se le proporcionan
* Casos de uso: Automoviles automaticos, relojes inteligentes, agricultura, perfil financiero, correos electronicos

**Servicios de inteligencia artificial en AWS**
* **Amazon Kendra** ofrece un sistema de búsqueda inteligente a nuestros clientes
* **Amazon Personalize** brinda recomendaciones personalizadas a nuestros clientes

**Servicios de analisis de métricas comerciales**
* **Amazon Lookout for metrics** detecta automáticamente cambios inesperados en aspectos como el rendimiento de los ingresos y la retención de los clientes, ayudándonos a identificar la causas
* **Amazon Forecast** nos ayuda a crear modelos de pronósticos precisos
* **Amazon Fraud Detector** identifica actividades en línea potencialmente fraudulentas

**Servicios de visión artificial**
* Amazon Rekognition permite analizar imágenes, videos y extraer el significado de estos. 

**Servicios de idiomas**
* **Amazon Polly** ayuda a convertir el texto en un habla realista
* **Amazon Transcribe** permite agregar traducciones de voz a texto de calidad
* **Amazon Lex** permite generar agentes conversacionales o bots de chat
