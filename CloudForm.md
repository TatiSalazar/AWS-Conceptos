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

``.json
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
``
