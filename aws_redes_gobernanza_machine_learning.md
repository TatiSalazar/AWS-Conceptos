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

## Redes en la nuve
* **Amazon Virtual Private Cloud** permite definir y aprovisionar una red privada para nuestros recursos de AWS
* **AWS Transit Gateway** Permite conectar VPC con los recursos locales (on-premises) mediante un hub central
* **AWS PrivateLink**  proporciona conectividad privada entre las VPC y aplicaciones locales, sin exponer el tráfico al Internet público
* **Amazon Route 53** permite alojar nuestro propio DNS administrado

## Redes a escala
* Estos servicios nos permiten escalar el tráfico de red según las necesidades:
* **Elastic Load Balancing** permite distribuir automáticamente el tráfico de red a través de un grupo de recursos, con el fin de mejorar la escalabilidad
* **AWS Global Accelerator:** redirige el tráfico a través de la red global de AWS para mejorar el rendimiento de las aplicaciones globales
* **Amazon CloudFront** entrega de forma segura datos, videos y aplicaciones a clientes de todo el mundo con baja latencia.

