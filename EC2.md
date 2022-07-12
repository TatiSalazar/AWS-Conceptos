# EC2 (Elastic Compute Cloud)
* Es uno de los mas populares de la oferta de AWS
* Infraestructura como servicio
* Es fundamental para entender como funciona la nube

* Alquilar maquinas virtuales: 
* Escalar los servicios utilizando un ASG : contiene un conjunto de instancias EC2 que comparten características similares y se tratan como una agrupación lógica
* Almacenamiento de datos EBS: ELASTIC BLOCK STORE, proporciona volúmenes de almacenamiento de nivel de bloque para su uso con instancias de EC2
* Distribucion de carga entre máquinas (ELB): distribuye automáticamente el tráfico de aplicaciones entrantes entre varios destinos y dispositivos virtuales en una o varias zonas de disponibilidad (AZ).

* Linux
* Mac Os
* Windows

* Potencia de computo y nucleos CPU
* Memoria de accedo aleatorio RAM
* Espacio de almacenamiento
* Tarjeta de red
* Reglas de Firewall
* Accion de arranque

## EC2 User Data
* Script de datos de usuarios
* Actualizaciones, Software, Descarga de archivos
* Ejecuta usuario root

## EC2 tipos de instancias

* c3.large
* c -> familia aws
* 3 -> generacion de la instancia
* large -> tamaño

Tipos de instancias

## General Purpose:
Para proyectos como paginas web o repositorios de código.

## Compute Optimized:
* Carga de trabajo de procesamiento por lotes
* Transcodificación de medios
* Servidores web de alto rendimiento
* Informática de alto rendimiento (HPC)
* Modelado científico y Machine Learning
* Servidores de Juegos dedicados

## Memory Optimized:
* Bases de datos
* Cache Distribuido
* Aplicaciones BI
* Aplicaciones para procesamiento en tiempo real

## Storage optimized:
* Procesamiento de transacciones (OLTP)
* Bases de datos relaciones y NoSQL
* Redis (Cache DB en memoria)
* Almacenamiento de datos

## Grupos de seguridad

* Trafico entrante ->
*                       Security group
* Trafico saliente <-
* Fundamentales para la seguridad.
* Reglas de permisos para trafico entrante/saliente (firewall)
* Es un componente que se adjunta a las intancias EC2.
* Puedes referenciar grupos de seguridad entre si.

* Puertos clasicos
* 21 ftp
* 22 ssh
* 22 sftp
* 80 http
* 443 https
* 3389 RDP
