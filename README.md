# AWS-Conceptos
# AWS
Definiciones, conceptos sobre aws

## IAM: Usuarios y grupos

* **IAM**: Gestión de acceso e identiedad global.
* **Root Account**: creada de manera prederteminada, no debe usarse ni compartirse
* **Usuarios**: Son personas dentro de su organización y se pueden agrupar
* **Grupos**: solo contienen usuarios, no otros grupos.
* **Los usuarios** no tienen que pertenecer a un grupo, y el usuario puede pertenecer a varios grupos
(IAM)

## IAM: Politicas
* Son los accesos a todos los servicios de AWS, y estas politicas van a ser dadas a traves de los usuarios o grupos se les pueden asignar documentos JSON llamados políticas.
* Estas politicas definen los permisos de los usuarios
* En AWS se aplica el principio de privilegios minimos (no otorgar mas permisos de los que necesita un usuario)

## Otorgar permisos
Se crea un usuario en los siguientes pasos:

1. IAM
2. Users
3. Add users
4. Asignar nombre y checkear los combobox (Acess key - password). Tambien en console password se checkea (Custom  password). Finalmente en Require password reset se checkea (User must create a new password)
5. Set permisos -> Add user to group -> create group
6. Group name -> AdministratorAccess "Politica de seguridad" para ser administrador y tenga acceso a todos los servicios de aws
7. Add tags : son utilizados para idenficar de donde pertenecen los recursos -> Next -> Create user
8. Download .csv (descargar la llave)
9. FIN

## Politicas IAM
* Una buena práctica recomendada por AWS es que las políticas se creen y se asocien a los grupos. Esto con el fin de poder administrar fácilmente los usuarios cuando exista una cantidad considerable.

Estructura:
* Versión
* Id : id para la politica
* Declaración: 1 o más
  * Sid: id
  * Efecto: permite o deniega el acceso
  * Principal: cuenta/usuario/rol al que se le aplica la politica
  * Acción: lista de acciones
  * Recurso: lista de recursos
  * Condición: condiciones (opcional)
 
## Politica de contraseñas
 * Contraseñas seguras
 * Longitud minima de contraseña
 * Tipo de caracteres especificos
 * Cambien sus propias contraseñas
 * Caducidad de contraseña
 * Reutilizar contraseñas

##  Autenticacion Multifactor o MFA
* Los usuarios tienen acceso a su cuenta y posiblemente cambiar configuraciones o eliminar recursos en su cuenta de AWS
* Quiere proteger sus cuentas raiz y usuarios de IAM
* MFA = contraseña que conoce + dispositivo de seguridad que posee

## Opciones de dispositivo MFA en AWS
**Dispositivo virtual:**
 * Google Authenticator (unico dispositivo)
 * Authy (Multidispositivo)
 
**Factor universal**
 * Yubikey by Yubico
 
**Dispositivo MFA de llavero de hardware**
 * Provided by Gemalto
 
 **MFA de llavero para AWS GovCloud en US**
 * provided by SurePassID

## Como los usuarios pueden acceder a AWS

**CLI**
* Heramienta que le permite interacturar con los servicios de AWS mediante comandos en su shell de linea de comandos
* Acceso directo a la API publicas de los servicios de AWS
* Puede desarrollar scripts para administrar sus recursos
* Es de código abierto github

**SDK de AWS**
Software Development kit de aws con diferentes librerias y lenguajes de programación.
* c++
* javascript
* go
* python
* .net
* java
* ruby
* php

## Setup AWS CLI en Windows

1. AWS CLI installer (buscar en google)
2. Entrar en la pagina oficial de aws y descargar el instalador
3. Abrir el .msi e instalar (todo darle next)

**Configurar cli y Access Key**
1. Iniciar sesion en root
2. entrar en IAM, en la parte derecha en el manu Aws account copiarmos el **link** 
3. pegamos el link en otro navegador e iniciamos sesion con la cuenta creada antes
4. entrar a my security credentials 
5. el usuario que quiere ingresar debe estar en el grupo de "administradores", si no lo está, con la cuenta root debemos de cambiarlo.
6. entrar a my security credentials, create access key y secret key (descargar .csv)
7. entrar a la terminal -> 
8. comando: aws configure  -> el cual pide la access key y secret key ->
9. pide region (cualquiera donde vamos a trabajar) -> us-east-1 -> None (enter)
10. Finish
11. comando: aws iam list-users 
12. muestra un json con el usuario y toda su info
13. Ya esta todo configurado, por lo tanto ya se puede utilizar todos los servicios de aws dentro de la terminal

## AWS CloudShell

Es para los que no quieren descargar el CLI en sus computadores, pero solo esta disponible en algunas pocas regiones.

1. Entro con mi usuario en aws y voy al item AWS Management Console
2. Click en el icono del terminal y se abre la consola
3. Hacer todos los pasos anteriores (setup cli windows)
5. Finish


## Roles en IAM para servicios

* Algunos servicios de AWS deberán realizar acciones en su nombre
* Para ello, asignaremos permisos de aws con roles de iam
* Roles comunes:
 * Roles de la instancia EC2
 * Roles de la funcion Lambda
 * Roles para CloudFormation

## Herramientas de seguridad
* Reporte de credenciales
* Asesor de acceso

**Credential Report**
Nos ofrece un reporte completo de lo que esta haciendo nuestros usuarios un excel

**Access Advisor**
En el menú Users -> Acess Advisor -> se lista y se visualiza los ultimos servicios que ha utilizado nuestros usuarios.

## Mejores Prácticas

**No usar la cuenta ROOT :** Para crear servicios, solo usar esta cuenta para configurar nuestros usuarios, por ejemplo, la cuenta administrador para crear los servicios y otros usuarios
**Un usuario fisico = Un usuario AWS**
**Asignar Usuarios a Grupos:** para administrar mas facil a los usuarios
**Crear politicas para contraseñas** por ejemplo, usar caracteres especiales, mayusculas, minusculas, etc.
**Multi Factor Authentication** para tener mejor seguridad en nuestra cuenta
**Crear y usar roles**
**Usar Access Keys para accesos programaticos**
**Informe de credenciales de IAM** ver los reportes de que hacen nuestros usuarios
**Nunca compartir usuarios y access keys** entre los developers
















