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

video 5 lab
