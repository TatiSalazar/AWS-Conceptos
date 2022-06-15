# Introduccion a AWS - Fundamentos de Cloud Computing

Un **servidor** está compuesto de un :
* Cliente : Tienen direcciones IP
* Network : Es el intermediario entre el cliente y el servidor
* Servidores : Tienen direcciones IP
  * Cómputo: CPU es utilizado para hacer todas las operaciones que necesitamos para   nuestra información
  * Memoria: RAM va almacenar esa información va poder ser como un gran cerebro que   se ocupa de esa información
  * Almacenamiento: datos, datos almacenan datos, los datos son como archivos de       texto plano que ocuparemos
  * Base de datos: información almacenada de forma estructurada
  * Redes: routers, switch, servidor DNS

**Terminología de IT**
* Redes: cables, routers y servidores conectados unos a otros.
* Router: un dispositivo de red que reenvía paquetes de datos entre redes informáticas.
* Switch: toma un paquete y lo envía al servidor/cliente correcto en la red.

**Diseño de infraestructura “tradicional”**
* Garage, con un servidor, dos servidores -> oficinas -> data centers

**Problemas del enfoque de IT Tradicional**
* Renta
* Mantenimiento
* Reemplazar y agregar hardware
* Escalamiento limitado
* Contratar 24/7 para monitorear
* Desastres naturales

**Ventajas del Cloud Computing**
* Menores costos: no se incurre en gastos de espacio, mantenimiento, hardware
* Mayor escalabilidad: uso eficiente de los recursos necesarios sin importar el tamaño o crecimiento del proyecto
* Confiabilidad: soporte tecnico 24/7, proteccion contra eventualidades y/o desastres naturales 
* Cambiar la inversion de capital por gastos variables
* Beneficiarse de las grandes economias de escala
* Dejar de hacer suposiciones sobra la capacidad
* Aumentar la velocidad y la agilidad
* Dejar de gastar dinero en la ejecucion y el mantenimiento de centros de datos
Adquirir escala mundial en minutos

## Tipos de cómputo en la nube

* **IaaS**: Infraestrucura como Servicio. 
  * Azure
  * Linode
  * Digital Ocean 
  * S2 AWS 
  * 
* **PaaS**: Plataforma como Servicio.
  * Heroku
  * Google App Engine
  * AWS Elastic Beanstalk 
  * Firabase
  
* **SaaS**: Software como Servicio.
  * Amazon Rekognition
  * Dropbox
  * Zoom
  * Gmail
 
* **On-premise**
    Applications: si
    Data: si
    Runtime: si
    Middleware: si
    O/S: si
    Virtualization: si
    Servers: si
    Storage: si
    Networking: si
 
## Precio nube, AWS

* Computo, pagar por el tiempo que usamos la computación
* Almacenamiento, pagar por la información almacenada en la nube
* Información, información transferida fuera de la nube

## Historia de AWS

Benjamin Black y Chris Pinkham querian solucionar el problema de cuando alcanzaran el tráfico mas alto en la página

* 2002: Internamente lanzado
* 2003: La infraestructura de Amazon es una de sus principales fortalezas idea para comercializar
* 2004: Se lanza al público SQS
* 2006: Se relanza al público SQS, S3 y EC2
* 2007: Se lanza en Europa
* 2009: Se lanza RDS
* 2010: Se lanza route 53
* 2012: Se lanza DynamoDBThe future… no lo sabemos

# AWS en números
AWS tuvo $35.02 mil millones en ingresos anuales en 2019.
AWS representó el 47% del mercado en 2019 (Microsoft es 2º con 22%)
Mas de 1.000.000 de usuarios activos dentro de aws

## Cómo escoger una región de AWS

* **Cumplimiento** de los requisitos legales y de gobernanza de datos: los datos nunca abandonan una región sin su permiso explícito.
* **Proximidad a los clientes**: latencia reducida.
* **Servicios disponibles** dentro de una región: los nuevos servicios y las nuevas funciones no están disponibles en todas
las regiones.
* **Los precios** varían de región a región y son transparentes en la página de precios del servicio.

## Una zona de disponibilidad es un data center
* Un data center está lleno de servidores
* Una zona de disponibilidad puede ser de varios data center.
* Cada zona de disponibilidad es uno o mas centro de datos discretos con energía, redes y conectividad redundante, están separados entre sí y están conectados entre sí con un gran ancho de banda, redes de latencia ultrabaja

## Infraestructura
* AWS Regiones
* AWS Zonas de disponibilidad
* AWS Centro de datos
* Ubicaciones de AWS Edge / puntos de presencia

## Infraestructura Global (Servicios)
* IAM
* Route 53
* Cloudfront
* WAF

## Servicios Regionales
* EC2
* Beanstalk
* Lambda
* Rekognition

Diagrama del modelo de responsabilidad compartida
* AWS:
 * hardware y la infraestructura global
    * Regiones (regions)
    * Zonas de disponibilidad (availability zones)
    * Ubicaciones de AWS Edge / puntos de presencia (Edge locations)
  * Software:
    * computo (compute)
    * almacenamiento (storage)
    * bases de datos (database)
    * redes (networking)
* Cliente:
  * Actualizaciones de S.O.
  * Proteger los datos que se almacenan
  * Aplicaciones
  * Accesos
  * Administración de usuarios y grupos

## Protección de datos
* Amazon Macie: para descubrir y proteger sus datos sensibles
* AWS Key Management Service: almacena y administra claves de cifrado
* AWS CloudHSM: almacenamiento de claves basado en hardware y el cumplimiento normativo
* AWS Certificate Manager, provisiona, administra e implementa certificados de seguridad TSL y TLS
* AWS Secrets Manager: rotar, gestionar y recuperar secretos como contraseña

## Protección de la infraestructura
* AWS Shield, para la protección de denegación de servicio
* AWS Web Aplication Firewall, (WAF) filtra el tráfico de sitios web maliciosos
* AWS Firewall Manager, administra las reglas del firewall de forma centralizada

## Deteccion de amenazas
* Amazon GuarDuty, detecta amenazas automáticamente
* Amazon Inspector, ayuda a analizar la seguridad de la aplicación
* Amazon config, registra y evalúa configuraciones de nuestros recursos
* Amazon CloudTrail, rastrea la actividad del usuario y el uso de las API

## Gestion de identidades
* AWS Identity and Access Management, (IAM) administra de forma segura el acceso a una cuenta, servicios y recursos
* AWS Inicio de sesión único: Implemente el acceso de sesión único (single sign on)
* AWS administra la identidad dentro de las aplicaciones, se puede hacer el inicio de sesiones moviles
* AWS Servicio de Directorio, implementa y administra un Active Directory Service
* AWS Organizaciones, para gobernar y administrar de forma centralizada en un mismo lugar

## IAM
AWS Identity and Access Management (IAM) proporciona un control de acceso detallado en todo AWS.
* Nos ayuda a administrar quién puede acceder a qué en los servicios y recursos de tu cuenta en AWS
* Puedes crear usuarios y grupos
* Establecer permisos permitir o denegar el acceso a los recursos de AWS mediante el uso de políticas
* IAM es gratuito y esta disponible en todo aws

## Usuarios IAM

1. Root User: Principal, acceso a todo aws, y crea usuarios IAM
2. Se crean otros roles, por ejemplo, developers, sales, tester. Se pueden crear **politicas**, creando grupos de acceso.

## IAM Roles
Se crean roles, por ejemplo, rol developer, rol tester, para poder ingresar a algun servicio en especifico.

## Acerca del servicio (AWS Secrets Manager)

El servicio le permite alternar, administrar y recuperar fácilmente credenciales de bases de datos, claves de API y otros datos confidenciales durante su ciclo de vida. Los usuarios y las aplicaciones recuperan datos confidenciales con una llamada a las API de Secrets Manager, lo que elimina la necesidad de codificar información confidencial en texto sin formato.

* Protege los secretos que son necesarios para acceder a sus aplicación, servicios y recursos.
* Rotarlos automáticamente 
* Los secretos pueden ser contraseñas, claves y tokens

```java
import mysql.connector
connection = mysql.connector.connect(
host="localhost",
database="mydb",
user="root",
password=get_secret_value['SecretString'])
```

## AWS Directory Service
Es una oferta de servicio administrado de AWS que le proporciona:
* Directorio activo administrado
* Opción de directorio activo simple
* Conector AD
* Servicio distribuido con error automático
* Compatible con otros servicios de AWS

 ## Crea una alerta de facturación
 Proceso de configuracion:

1. click en el nombre de usuario
2. click en opcion: Billing Dashboard
Budgets
3. Create a Budgets
4. Nos mostrara los Budget Types, dejar amarcada la opcion por defecto Cost budget -Recommended y click en el boton superior: Enable cost Explorer para habilitar el seguimiento de gastos
5. En la pagina de budget types, dar click en next
nos mostrara la pagina Set Your Budget
seleccionar cada cuando se realizara el budget, daily, monthly, etc
6. seleccionar desde cuando se quire empezar a hacer el monitoreo en Start Date
7. seleccionar en Choose how budget. Fixed significa que va monitorear si nos gastamos mas o igual de la cantidad indicada en el campo Enter your budgeted amount($)
8. click en Next
9. Click en el boton: Add an alert threshold
10. En la seccion Alert #1, configuraremos como se debe ejecutar la alerta
11. Indicamos si la alerta se hara por el valor absoluto o algun porcentaje en Email recipients indicar el correo electronico al que llegara la alerta
12. click en: Add alert threshold
13. click en: Create budget
