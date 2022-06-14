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
