# DOCKER: Practic guide for developers

### Instalaciones previas
https://gist.github.com/Klerith/3f611ff0e5c15b733ac63365ab310a35

## ¿Qué es Docker? 
### Antes de Docker

Antes de Docker, al incorporar un nuevo desarrollador a un proyecto era habitual tener que instalar manualmente todas las herramientas necesarias para el entorno de desarrollo. No solo era necesario instalar bases de datos, motores de caché, brokers de mensajería o cualquier otra dependencia, sino también versiones muy específicas de cada una de ellas. Esto era especialmente importante en aplicaciones legacy, donde una actualización mínima podía romper la compatibilidad. Como consecuencia, **todos los integrantes del equipo debían mantener exactamente las mismas versiones para garantizar que el proyecto funcionara de la misma manera en todos los entornos**.

El **problema se volvía aún más complejo** cuando un mismo desarrollador trabajaba desde varias computadoras (por ejemplo, una desktop y una notebook) o cuando el equipo utilizaba distintos sistemas operativos, como Windows, Linux o macOS. **Cada plataforma tiene diferencias en la instalación de software, compatibilidad de versiones, administración de dependencias e incluso disponibilidad de determinadas herramientas**, por lo que era común encontrarse con errores que solo ocurrían en un sistema operativo determinado.

A esto se sumaba otro escenario frecuente: trabajar simultáneamente en varios proyectos. **Cada aplicación podía requerir un conjunto completamente distinto de dependencias y versiones**, por lo que mantener todos esos entornos correctamente configurados terminaba siendo una tarea compleja, propensa a errores y difícil de mantener.

Una alternativa era utilizar máquinas virtuales, ya que permitían aislar completamente el entorno de cada proyecto. Sin embargo, una máquina virtual emula una computadora completa, incluyendo el kernel del sistema operativo, la interfaz gráfica, servicios del sistema y muchos otros componentes que la aplicación realmente no necesita para ejecutarse. Como consecuencia, las máquinas virtuales consumen una cantidad considerable de memoria, espacio en disco y recursos del procesador. Además, requieren más tiempo para iniciarse, apagarse, copiarse o distribuirse entre distintos equipos, haciendo que la experiencia de desarrollo resulte mucho más pesada.

### Con Docker

``Docker resuelve este problema mediante el uso de imágenes y contenedores.``

**Una imagen puede entenderse como una plantilla inmutable que contiene todo lo necesario para ejecutar una determinada tecnología o aplicación: el sistema de archivos, las dependencias, las configuraciones y la versión exacta del software que queremos utilizar.**

A partir de una imagen se crea un contenedor, que es **una instancia en ejecución de esa imagen**. Cada contenedor funciona de manera aislada, sin interferir con los demás, permitiendo ejecutar simultáneamente distintas tecnologías e incluso diferentes versiones de una misma herramienta.
De esta forma, **si un proyecto necesita una versión específic**a de una base de datos y otro proyecto utiliza una completamente diferente, ambos entornos pueden coexistir sin conflictos, ya que **cada uno ejecuta sus propias dependencias dentro de sus respectivos contenedores**.

Además, **Docker abstrae las diferencias entre los sistemas operativos anfitriones**. Independientemente de si un desarrollador utiliza Windows, Linux o macOS, el contenedor se comportará de la misma manera, ya que Docker **se encarga de proporcionar un entorno de ejecución consistente**.
Esto permite que todos los miembros del equipo trabajen sobre exactamente el mismo entorno, reduciendo los clásicos problemas de configuración, eliminando las diferencias entre máquinas y facilitando enormemente la incorporación de nuevos desarrolladores al proyecto.

## Beneficios
`A diferencia de las máquinas virtuales, los contenedores se levantan en milésimas de segundos o segundos`
- Cada contenedor está aislado de los demas.
- Es posible ejecutar varias instancias de la misma versión o diferentes versiones sin configuraciones adicionales.
- Con un comando, se puede descargar, levantar y correr todo lo que necesites.
- Cada contenedor contiene todo lo que necesita para ejecutarse.
- Es indiferente el sistema operativo HOST

### Flujo de trabajo usando Docker
Supongamos que estamos trabajando en una API y frontend necesita empezar a consumirlo y nosotros necesitamos empaquetar nuestra aplicación y distrubuírla
- Generamos nuestra imagen desde el back, hacemos el build process,  el cual se puede automatizar meidante Git y Jenkins para el proceso de construcción de nuestra imagen, -que tambien automatiza el siguiete paso-.
- Construimos la imagen (ahí ya estaría node instalado, la app instalada con únicamente las dependencias de prod.), la imagen contiene todo lo que yo necesito para ejecutar.
- Esta imagen se sube a un repositorio (container, parecido a Github, pero pensado específicamente para imágenes de Docker)
- El servidor hace el pull de la imagen y ya esto tiene todo lo que nosotros necesitabamos para correr aplicaicón específicamente como se necesita, así como el front se descarga la imagen y tiene la capacidad de correrla localmente.

[Imagen](/doc/image.md)