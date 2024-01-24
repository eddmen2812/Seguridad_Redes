# Ejercio con OPNSense
## Filtrado Web con OPNSense.
* Implementar un proxy transparente usando SQUID y SQUIDGUARD en la plataforma OPNSENSE que permita realizar control de acceso web a los usuarios de una red LAN.
* Monitorización constante: Establecer un sistema de monitoreo de tráfico de red para detectar patrones de tráfico anormales o inusuales que puedan indicar un posible ataque EIGRP. Esto permite una respuesta rápida en caso de un incidente.
* Segmentación de red: Dividir la red en segmentos lógicos o VLANs y aplicar controles de acceso adecuados para limitar la propagación de paquetes EIGRP maliciosos. La segmentación ayuda a evitar que un ataque se propague por toda la red.
* Actualización de firmware y parches: Mantener el firmware y el software de enrutadores y dispositivos de red actualizados con las últimas actualizaciones y parches de seguridad. Los ataques a menudo se aprovechan de vulnerabilidades conocidas, por lo que mantener actualizado a un sistema es crucial

## Conceptos básicos
* El paquete Squid en OPNsense es un servidor proxy transparente que se utiliza para mejorar el rendimiento y la seguridad de la red. Algunas de las funciones y características clave de Squid en OPNsense incluyen:
    * **Caché de reenvío:** Squid puede almacenar en caché y reutilizar páginas web frecuentemente solicitadas, lo que reduce el ancho de banda y mejora los tiempos de respuesta.
    * **Control de acceso:** Squid puede utilizarse para autenticar a los usuarios y aplicar listas de control de acceso (ACL) para filtrar el tráfico web basado en categorías o reglas personalizadas.
    * **Proxy transparente:** Squid puede configurarse como un proxy transparente, lo que significa que los clientes no necesitan realizar ninguna configuración especial para utilizarlo. El tráfico web se enruta automáticamente a través del proxy sin que los usuarios sean conscientes de ello.
    * **Filtrado de contenido:** Squid puede utilizarse junto con SquidGuard para aplicar políticas de filtrado de contenido y bloquear el acceso a sitios web no deseados o peligrosos.
    * **Registros y estadísticas:** Squid registra información detallada sobre el tráfico web, lo que permite generar informes y estadísticas para analizar el uso de la red.
    
### A continuación, se realiza levantamiento de laboratorio para trabajar en entornos controlados.

![Alt text](image.png)

Ingresamos a la interfaz gráfica de OPNSense para sus respectivas configuraciones

   ![Alt text](image-1.png)

Una vez configurado todo, se nos desplegará la siguiente pantalla que nos Ayudará a visualizar la exitosa instalación y de paso actualizamos al sistema

![Alt text](image-2.png)

Procedemos actualizar

![Alt text](image-3.png)

Actualizado a la última versión

![Alt text](image-4.png)

OPNSense ya viene habilitado para que los clientes tengan acceso a internet

![Alt text](image-5.png)

Ya instalado el OPNSense implementamos un proxy transparente usando SQUID y SQUIDGUARD en la plataforma OPNSENSE que permita realizar control de acceso web a los usuarios de una red LAN. 

---
### Filtrado Web

Para una mejor guía, siempre es bueno basarnos en la documentación oficial de OPNSense: [¡Da click para ir a la página oficial!](https://docs.opnsense.org/manual/how-tos/proxytransparent.html "Información Adicional")

Para que todo funcione, hay que verificar el certificado SSL que es esencial para garantizar la seguridad y la privacidad de las comunicaciones en línea. Ayuda a prevenir el robo de información y protege a los usuarios contra posibles ataques cibernéticos. En caso de que no este creado, se procedería a crearlo.

![Alt text](image-6.png)

Esta certificación se tiene que descargar e instalarla en los equipos host pero en nuestro caso omitiremos dicha instalación
Verificamos que aún no está instalado el squid

![Alt text](image-7.png)

--- 
### Instalación de SQUID
Nos vamos a la configuración general del proxy y habilitamos con el respectivo squid

![Alt text](image-8.png)

También hay que habilitar lo siguiente

![Alt text](image-9.png)

Una vez configurado no redirigimos Al local cache

![Alt text](image-10.png)
![Alt text](image-11.png)
![Alt text](image-12.png)

Agregamos una nueva regla pero dejaremos por default todo

![Alt text](image-13.png)

Ahora ya tenemos una nueva regla creada y daremos click en guardar cambios

![Alt text](image-14.png)

Ahora nos regresamos al forward proxy y habilitamos

![Alt text](image-15.png)

Para verificar el servicio del squid, vamos al Dashboard

![Alt text](image-16.png)

---
#### Control de acceso web
Como prueba tendremos denegado el acceso a whatsweb, facebbok, Instagram y Telegram.

Ahora lo único que hay que hacer es agregar un alista de control de acceso.

![Alt text](image-17.png)

Dijitamos las páginas de denegar en la lista negra de páginas

![Alt text](image-18.png)

---
#### Pruebas en clientes
La desventaja de esto esque con squid hay que configurar el proxy en cada cliente para aplicar el filtrado web.

![Alt text](image-19.png)
![Alt text](image-20.png)
![Alt text](image-21.png)

Toda página registrada deniega el tráfico y como youtube no se listo, se puede tener acceso sin restrincción.

![Alt text](image-22.png)

**La ventaja de OPNSense esque viene incorporado un sistema de logs, en donde podremos ver todo el registro generado por parte de clientes.**

En este laboratorio se introdujeron dos clientes para prueba con ip 192.168.1.101 y 102

![Alt text](image-23.png)

En OPNSense se visualiza el historial de cada uno de los clientes.

![Alt text](image-24.png)

Como se puede ver, para filtrar la web hay que dijitar manualmente cada dirección web y es algo tedioso. Para mejorar este filtrado tenemos el squidguard. Que contiene un listado de muchas páginas y es más fácil su administración y control.

---
### Instalación de SQUIDGUARD
En esta ocasión crearemos un certificado de autoridad para ser descargado en la máquina host para que valide y no estar que digitando en los navegadores la ip y el puerto del proxy.

Creamos el certificado

![Alt text](image-25.png)
![Alt text](image-26.png)

Una vez creado el certificado procedemos a descargarlo en el host

![Alt text](image-27.png)

Instalamos el certificado en entidades de certificación de confianza

![Alt text](image-28.png)
![Alt text](image-29.png)

Habilitamos la opción de OPNSense y aplicamos los cambios

![Alt text](image-30.png)

Habilitamos proxy transparente  para http y http y salgan por los puertos 3128-3129

![Alt text](image-31.png)

Y escogemos la certificación creada anteriormente
![Alt text](image-32.png)
![Alt text](image-33.png)

Verificamos las reglas creadas

![Alt text](image-34.png)

Descargamos el squirdguard y aplicamos cambios

![Alt text](image-35.png)
![Alt text](image-36.png)

Nos dirijimos al firewall a crear las reglas para http y https

![Alt text](image-37.png)

Lo mismo para el puerto 443

![Alt text](image-38.png)

Ahora movemos las reglas a primer lugar para que sea lo primero que deban respetar los hosts.

![Alt text](image-39.png)

#### Ahora solo probamos en el cliente la navegación.

En Disney tenemos acceso, pero redes sociales y bitcoins están bloqueadas, tal y como descargamos el squidguard

![Alt text](image-40.png)

