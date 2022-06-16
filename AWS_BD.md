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

## Instancias Reservadas

## 
