# CloudFormation
AWS CloudFormation es :
* Un servicio que lo ayuda a modelar y configurar sus recursos de AWS
* Menos tiempo dedicado a la administracion de dichos recursos
* Se crea una plantilla que describa todos los recursos de aws que desee y cloudformation se encarga del aprovisionamiento y configuracion de dichos recursos.

## Simplificacion de la administracion de la infraestructura
* Para una aplicacion web escalable que tambien incluye una base de datos backend, se podría usar **Auto Scaling**, un equilibrador de carga **Elastic Load Balancing** y una instancia de BD de Amazon Relational Database Service. Todos estos servicios se puede configurar pero es mas complejo, por esta razon se usa una *plantilla de cloudFormation*.
* **Una plantilla de CloudFormation** describe todos los recursos y las propiedadees de estos.  
* Cuando se crea una pila **CloudFormation** aprovisiona los recursos que se describen en su plantilla.
* Despues de crearse la **pila** los recursos de aws se crean, y si se quiere eliminar, se eliminan todos los recursos creados.
* Con **CloudFormation** es facil administrar un conjunto de recursos como una unica unidad. 

## Replicación rápida de la infraestructura
* **CloudFormation** usarlo para crear sus recursos de una manera consistente y repetible
* para reutilizar las plantillas tiene que describir los recursos una vez 

## Control y seguimiento sencillos de los cambios en la infraestructura
* Se puede utilizar el **Auto Scaling** para pasar una instancia de mayor rendimiento 
* **CloudFormation** describe exactamente que recursos se aprovisionan y su configuracion.
* Pueden guardar las versiones de las plantillas para llevar un seguimiento de cambios de la infraestructura.

# Plantillas
* Una plantilla CloudFormation es un archivo de texto en formato JSON o YAML 
* Con las extensiones .json .yaml .template .txt
* Son utilizadas para crear recursos de aws
* Ejemplo:

```json
{
  "AWSTemplateFormatVersion" : "2010-09-09",
  "Description" : "A sample template",
  "Resources" : {
    "MyEC2Instance" : {
      "Type" : "AWS::EC2::Instance",
      "Properties" : {
        "ImageId" : "ami-0ff8a91507f77f867",
        "InstanceType" : "t2.micro",
        "KeyName" : "testkey",
        "BlockDeviceMappings" : [
          {
            "DeviceName" : "/dev/sdm",
            "Ebs" : {
              "VolumeType" : "io1",
              "Iops" : 200,
              "DeleteOnTermination" : false,
              "VolumeSize" : 20
            }
          }
        ]
      }
    }
  }
}
```
## Anatomia de una plantilla
* Describe una estructura del aws
* JSON estructura:

```json
{
  "AWSTemplateFormatVersion" : "version date",

  "Description" : "JSON string",

  "Metadata" : {
    template metadata
  },

  "Parameters" : {
    set of parameters
  },
  
  "Rules" : {
    set of rules
  },

  "Mappings" : {
    set of mappings
  },

  "Conditions" : {
    set of conditions
  },

  "Transform" : {
    set of transforms
  },

  "Resources" : {
    set of resources
  },
  
  "Outputs" : {
    set of outputs
  }
}
```
* YAML
```json
---
AWSTemplateFormatVersion: "version date"

Description:
  String

Metadata:
  template metadata

Parameters:
  set of parameters

Rules:
  set of rules

Mappings:
  set of mappings

Conditions:
  set of conditions

Transform:
  set of transforms

Resources:
  set of resources

Outputs:
  set of outputs

```

## Secciones de plantillas
* **Resource** : (Unica) Obligatoria.   
* **Version Formato** : (Opcional). Es diferente para API y WSDL
* **Descripcion** : (Opcional). Una cadena de texto que describe la plantilla.
* **Metadatos** : Objetos que dan informacion adicional sobre la plantilla.
* **Parámetros** : (Opcional) Valores que se van a pasar a la plantilla en tiempo de ejecucion (crear/actualizar pila)
* **Reglas** : (Opcional) Valida parametros durante la creacion o actualizacion de una pila.
* **Mapeos** : (Opcional) Un mapeo de claves y los valores asociados se pueden utilizar para especificar valors de condicionales "Similar a una tabla de busqueda"
* **Condiciones** : (Opcional) Condiciones que controlan si determinados recursos se crean o si a determinadas propiedades de recursos se les asigna un valor durante la creación de la pila o la actualización.
* **Transformación** : (Opcional) Para aplicaciones sin servidor (Lambda), especifica la versión de AWS SAM que hay que utilizar. Cuando especifique una transformación, puede utilizar sintaxis AWS SAM para declarar los recursos en la plantilla. El modelo define la sintaxis que puede utilizar y la forma en la que se procesa.
* **Recursos** : (Obligatorio) Especifica los recursos de la pila y sus propiedades.
* **Salidas** : (Opcional) Describe los valores que se devuelven siempre que ve las propiedades de su pila.


# CLOUDFORM

Lambda code -> Github -> Source -> Compilar -> Desplegar -> Lambda 

## Herramientas
* **Terraform** : despliegues multi cloud, posee una version open source y otra enterprise
* **Pulumi** : despligues multi cloud, podes sacar ventajas tus conocimientos en un lenguaje
* **Serverless Framework** : para el despliegue de Lambdas, dynamoDb, api gateway, s3, kinesis
* **SDK** : provista diferentes lenguajes, para python se llama boto3
* **CDK** : (Cloud Development Kit): diferencia con el sdk, es que no va usar librerias particulares, sino que dentro del mismo codigo python vamos a llamar a los recursos y crealos. Por detras cdk va a generar un template de CFN.
* **AWS SAM** : (Serverless Aplication Model): para el despliegue de Lambdas, dynamoDb, api gateway, kinesis. Cambia la definición del recurso, para desplegar una lambda en CFN se declara como “AWS::Lambda::Function” y en SAM “AWS::Serverless::Function”
## Versionamiento
Trazabilidad sobre el codigo, quien lo modifico, quien lo acepto
## Eficiencia
Desplegarlos en diferentese ambientes ( mejor tiempo)
Dev
Stg
Prd
## Re-Utilizable
Reutilizar infraestructura que hemos utilizado para otros proyectos
## Infraestructura Inmutable
No se puede cambiar
Si tenemos un error en la infraestructura, siempre es mejor desplegar de nuevo la infraestructura

# Ventajas y Beneficios

**Code -> Check -> Create -> Deploy**

* Template  -> JSON, YML
* Servicios -> Stacks, Stack Set y Designer

* Flujo de despliegue : código, se verifica y hay una fase de despliegue. Se pueden crear templates en formato YAML o JSON.
* Servicios : Stacks, stack sets, integración full con todos los componentes de AWS.
* Beneficios :  AWS brinda soporte sobre tu código de cloudformation en caso de que no despliegue tu integración, es decir brinda soporte sobre tu código si tienes el plan bussiness contratado.
* Integración nativa con todos los servicios de AWS.
* Designer: te permite crear infraestructura de forma visual y si ya lo tienes creado, cargas tu plantilla y veras como luce.
* Multicuenta: desplegar en 3 cuentas diferentes la misma infraestructura.
* Flexibilidad: creación de recursos dinámicamente con custom resources.
* Cloudformation: gratis, se te cobra por los recursos que este despliegue.
* Escalabilidad: puede crecer desde el recurso mas simple hasta una arquitectura más compleja.
* Seguridad: todos los despliegues están completamente asegurados, cifrado de llaves, etc.
* Estabilidad: al ser administrado por AWS tiene un alto nivel de SLA.
* Transaccional: espera a que todos los recursos estén creados para desplegar la aplicación, sino hará un rollback.
* Empresa que usan Cloud Formation: Barcelona FC, Expedia, Coinbase, nextdoor.

# Template
* Especificar version
• AWSTemplateFormatVersion: “versión date”: Define las capacidades de la plantilla

* Opcional
• Description: String. Texto que describe la plantilla, es opcional.

* Opcional
• Metadata: Información adicional del template. Se pueden crear tres subregistros:
  AWS::CloudFormation::Init
  AWS::CloudFormation::Interface
  AWS::CloudFormation::Designer
  
* OPCIONAL/IMPORTANTE, son los valores que se le pasan a la plantilla cuando se crea o actualiza un stack. SON RECURSOS DENTRO DE AWS.
• Parameters: Valores que se le pasan al template cuando se crea o actualiza un Stack. Pueden ser referenciados desde Resources u Outputs.


´´´json
Parameters:
	myKeryPair:
		Description: Amazon EC2 Key Pair
		Type: “AWS::EC2::KeyPair::KeyName”
	mySubnetIDs:
		Description: Subnet IDs
		Type: “List<AWS::EC2::Subnet::Id>”
	DbSubnetIpBlocks:
		Description: “Comma-delimited list of three CIDR blocks”
		Type: CommaDelimitedList
		Default: “10.0.48.0/24, 10.0.112.0/24, 10.0.176.0/24”
	DBPort:
		Default: 3306
		Description: TCP/IP port for the database
		Type: Number
		MinValue: 1150
		MaxValue: 65535
	DBPwd:
		NoEcho: true
		Description: The database admin account password
		Type: String
		MinLength: 1
		MaxLength: 41
		AllowedPattern: ^[a-zA-z0-9]*$
´´´
* OPCIONA/ LLAVE VALOR QUE SE REFERENCIA DENTRO DEL TEMPLATE
• Mappings: Arreglos de llave valor asociados que se usan para agregar parámetros condicionales. Similar a una tabla de búsqueda. Utiliza la función Fn::FindInMap, Ej:

´´´json
Mappings:
	RegionMap:
		us-east-1:
			“HVM64”: “ami-0ff8a91507f77f867”
		us-west-1:
			“HVM64”: “ami-0bdb828fd58c52235”
´´´
* OPCIONAL/ si creamos o no un recurso / o si le asignamos una variable a un recurso
• Conditions: controlan si se crean ciertos recursos o si se asigna un valor a ciertas propiedades durante la creacion del stack.

* OPCIONAL
• Transforms: para aplicaciones serverless, si se especifica se pueden usar sintaxis de AWS SAM.

* OBLIGATORIO/
• Resources: especifica los recursos y las propiedades a crear, porque siempre vamos a desplegar un recurso. Campo obligatorio.

*OPCIONAL/**Si tus recursos quieres interconectar, los Outputs debes manejar.**
• Outputs: valores devueltos de las propiedades del recurso creado (DEL STACK), la funcion lambda toma el export de dynamo. ARN = Amazon Resource Name.

## ¿Que es un stack?
Coleccion de recursos que se manejan como unidad

## Gestion de recursos
CloudFormation asegura que todos los recursos sean creados o eliminados

## ¿Que pasa si un recurso falla en crearse?
Se hace rollback a todos los recursos del stack

## ¿Que pasa si borro un stack?
Todos los recursos asociados se borran

## ¿Que es un Drift?
Detecta una desviación entre el stack y los recursos desplegados

## ¿Que puedo identificar con un Drift?
Recursos agregados, eliminados y con propiedades diferentes

## Stack set

## ¿Qué tipos de cuentas existen?
Cuentas administrador y cuentas target

## ¿Desde dónde se despliegan recursos Multi Cuenta?
Se debe hacer desde una cuenta maestra que tenga permisos sobre las otras

## Instancias de un Stack
Hace referencia a un stack dentro de una cuenta

## Diferentes Parámetros
Se pueden desplegar stack set que cambien de parámetros dependiendo de la cuenta destino.

## NESTED STACKS
Surgen a causa de los limites de cloudformation
* 100 Mappings -> Stack
* 200 Recursos -> Stack
* 51,200 bytes -> Cuerpo de template para createStack, updateSatck, validateTemplate
* 460,800 bytes -> Tamaño máximo de template en S3

## Limites
Para crear recursos que necesiten pasar los limites de Cloudformation

## Granularidad
Cada recurso queda con un stack independiente

## Orden
Se pueden crear precedencias y condiciones entre recursos

## Intereaccion
Los stacks se comunican entre si a través de outputs

## -------------------------------------------------------------------------

## GetAtt
Devuelve el valor de un atributo de un recurso en el template
Cuando se quiere tomar algun atributo de un recurso dentro del mismo stack

Role: !GetAtt LambdaRole.Arn
LambdaRole -> Nombre logico del recurso
Arn -> atributo

## Composicion
Se compone del nombre del recurso y del atributo

## FindInMap

## Funcionalidad
Devuelve el valor correspondiente al map declarado en la seccion mappings

## Composicion
MapName, TopLevelKey y SecondLevelKey

```json
ImageId: !FindInMap
	- RegionMap  //MapName
	- !Ref 'AWS::Region' //TopLevelKey
	- HVM64  //SecondLevelKey
```

## Join
* Funcionalidad: Une un listado de valores en uno solo
* Composicion: Se compone de un listado de valores y un delimitador
* Sintaxis V1
```json
{ "Fn::Join" : [ "delimiter", [ list of values] ] }
```
* Sintaxis V2
```json
Fn::Join: [ delimiter, [ list of values] ] 
```
* Sintaxis V3
```json
!Join [ delimiter, [ list of values] ] 
```
## Split y Select
* SPLIT
* Dividir una cadena en una lista de valores
* SELECT
* Selecciona un valor de una lista de valores
```json
{ "Fn::Split" : [ "delimiter", "source string" ] }
```
```json
Fn::Split: [ delimiter, source string ] 
```
```json
!Split [ delimiter, source string ]  
```

* Sintaxis para SELECT
```json
{ "Fn::Select" : [ index, listOfObjects ] }
```
```json
Fn::Select: [ index, listOfObjects ] 
```
```json
!Select [ index, listOfObjects ]  
```
# Sub
* Funcionalidad: Sustituye una variable con un input que nosotros especifiquemos
* Composicion: String VarName: ValueName

```json
{ "Fn::Sub" : [ String, {Var1Name: Var1Value, Var2Name: Var2Value} ] }
```
```json
Fn::Sub:
 -String
 - {Var1Name: Var1Value, Var2Name: Var2Value}
```
```json
!Sub
 -String
 - {Var1Name: Var1Value, Var2Name: Var2Value}
```
## ¿Cuando usar Sub?
Cuando se requiera reemplazar un valor en un string, puede ser un pseudo parameter

* **AWS::AccountId** Numero de la cuenta de AWS
* **AWS::NotificationARNs** ARNs del stack actual
* **AWS::NoValue** Remueve un valor de la propiedad
* **AWS::Partition** Devuelve la particion de un recurso
* **AWS::Region** Devuelve la region actual del stack
* **AWS::StackName** Devuelve el nombre del stack
* **AWS::StackId** Devuelve el ID del stack
* **AWS::URLSuffix** Devuelve el sufijo de un dominio

!Sub 'arn:aws:ec2 ${AWS::Region}:${AWS::AccountId}:vpc/${vpc}
* ${AWS::Region} -> region actual del stack us-east-1

video 5,7,8,11,13,16,17  lab
