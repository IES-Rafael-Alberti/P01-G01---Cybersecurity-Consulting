# Cybersecurity Consulting

![Portada](./Assets/PORTADA.png)

# Índice

- [Introducción](#introducción)
- [Investigación de Vulnerabilidades](#investigación-de-vulnerabilidades)
  - [Fase 1: Categorías](#fase-1-categorías)
  - [Fase 2: Investigación de CVEs](#fase-2-investigación-de-cves)
- [Clasificación y análisis](#clasificación-y-análisis)
  - [Gravedad](#gravedad)
  - [Facilidad de explotación](#facilidad-de-explotación)
  - [Relevancia para TrustShield Financial](#relevancia-para-trustshield-financial)
- [Propuesta de contramedidas](#propuesta-de-contramedidas)
- [Conclusión](#conclusión)

<br><br>
# Introducción

La empresa TrustShield Financial confía en nosotros para llevar a cabo un análisis detallado de su infraestructura tecnológica, con el propósito de identificar vulnerabilidades críticas que pudieran comprometer la confidencialidad, integridad y disponibilidad de la información financiera. El enfoque principal ha sido en la categoría de tecnologías IoT, dado que estos dispositivos han adquirido una creciente relevancia tanto en el ámbito cotidiano como en entornos industriales, lo que los convierte en un objetivo potencialmente atractivo para agentes maliciosos. La interconexión de dichos dispositivos proporciona indudables beneficios, como la optimización de la eficiencia operativa y la generación de nuevas oportunidades comerciales; sin embargo, también introduce riesgos significativos en términos de seguridad, los cuales deben ser gestionados con la máxima diligencia.

<br><br>  
# Investigación de Vulnerabilidades
## Fase 1: Categorías

__Contraseñas débiles, adivinables o codificadas.__

Es común que muchos dispositivos cuenten con contraseñas fáciles de adivinar, como “1234” o “admin”. Estás contraseñas no ofrecen suficiente seguridad y si no se modifican, permiten un acceso fácil al dispositivo. Además, algunas contraseñas pueden estar codificadas u ocultas en el software del dispositivo, lo que deja la puerta abierta a posibles atacantes.
Un ejemplo es un router con la contraseña por defecto “Admin”, si no hacemos ningún cambio al respecto los ciberdelincuentes podrán acceder al dispositivo con facilidad.

__Servicios de red inseguros.__

Algunos dispositivos tienen habilitados servicios de red que no están adecuadamente protegidos o que no son necesarios para su principal funcionamiento. Estos servicios pueden comprometer el dispositivo ante ataque, especialmente si están abiertos a conexiones remotas.
Por ejemplo una impresora conectada a la red que tiene un servidor FTP por defecto, aunque no es necesario para su funcionamiento, puede ser explotada para robar información.

__Ecosistema de interfaces inseguras.__

Este tipo de vulnerabilidad no se encuentra directamente en el dispositivo, sino en las aplicaciones que interactúan con él. Un dispositivo seguro puede quedar expuesto si se conecta con una interfaz de software insegura.
Un ejemplo puede ser un smartwatch que es seguro por si mismo, pero que se conecta a una aplicación en un smartphone sin actualizaciones de seguridad, lo que expone la información personal del usuario a posibles ataques.

__Ausencia de un mecanismo de actualización seguro.__

Muchos dispositivos no cuentan con un sistema fiable para recibir actualizaciones de seguridad, o bien las actualizaciones se distribuyen de manera insegura, sin verificar la autenticidad del software, dejando espacio para la instalación del malware.
Por ejemplo  un dispositivo IoT que no puede recibir actualizaciones de seguridad automáticas o solo permite actualizaciones manuales a través de un canal no cifrado.

__Uso de componentes inseguros o desactualizados.__

Algunos dispositivos no continúan utilizando software o hardware con vulnerabilidades conocidas, lo que puede ser explotado por atacantes si no se actualizan o reemplazan. Este problema se ve agravado cuando los fabricantes utilizan componentes de bajo coste que no reciben actualizaciones de seguridad
Un ejemplo pueden ser cámaras de seguridad que funcionan con versiones obsoletas del firmware, dejando abierta brechas que ya han sido corregidas en versiones más recientes

__Insuficiente protección a la privacidad.__

Varios dispositivos no disponen de medidas adecuadas para proteger la privacidad de los datos personales que procesan, esto puede implicar la falta de encriptación, almacenamiento inseguro de datos o políticas de privacidad deficientes
Por ejemplo un altavoz inteligente que graba y almacena conversaciones sin el consentimiento del usuario o que no establecen mecanismos adecuados para proteger la información grabada.

__Transferencia y almacenamiento de datos inseguros.__

En muchos casos, los dispositivos no emplean protocolos de cifrado para la transferencia y el almacenamiento de datos, lo que permite que la información sensible sea interceptada o accedida por terceros no autorizados.
Un ejemplo puede ser un dispositivo de monitoreo de salud que transmite información sin cifrar a un servidor en la nube, lo que permite a los atacantes interceptar datos confidenciales.

__Ausencia de gestión de dispositivos.__

Cuando las organizaciones o usuarios no gestionan adecuadamente los dispositivos conectados a su red, se pierde el control sobre qué dispositivos están conectados y qué información manejan. Esto puede generar riesgos significativos si un dispositivo se conecta sin que se detecte por parte del personal.
Por ejemplo una empresa que no tiene sistema para monitorear cuantos dispositivos IoT están conectados a su red, permitiendo que un dispositivo comprometido actúe como puerta de entrada para un ataque a gran escala.

__Configuraciones por defecto inseguras.__

La mayoría de dispositivos que vienen con configuraciones predeterminadas son inseguras, como puertos abiertos, privilegios excesivos o servicios innecesarios activados. Si no se cambian estas configuraciones al instalar el dispositivo,  se deja expuesto a vulnerabilidades.
Un ejemplo puede ser un sistema de videovigilancia que al ser instalado, tiene habilitado por defecto el acceso remoto sin cifrado, lo que permitiría que un atacante intercepte las transmisiones de vídeo.


__Ausencia de seguridad física.__

Algunos dispositivos no tienen medidas de seguridad para evitar que personas no autorizadas realicen cambios físicos en el hardware. Al tener acceso físico al dispositivo, un atacante puede modificar el dispositivo y obtener datos sensibles o comprometer su funcionamiento.
Por ejemplo, un cajero automático que permite que al abrirlo físicamente, un atacante instale un dispositivo de clonación de tarjetas.

<br>

## Fase 2: Investigación de CVEs

### CVE-2020-15498
- Categoría: Ausencia de un mecanismo de actualización seguro.
- Descripción: Se detectó un problema en los enrutadores ASUS RT-AC1900P versiones anteriores a 3.0.0.4.385_20253. El enrutador acepta un   certificado de servidor arbitrario para una actualización de firmware. El culpable es la opción --no-check-certificate pasada a la        herramienta wget usada para descargar archivos de actualización de firmware.
- Gravedad: 5.9 Medium.
- Metodo de explotacion: Un atacante podría explotar esta vulnerabilidad de la siguiente manera:
  - Realizar un ataque de hombre en el medio (MITM) en la red del enrutador vulnerable.
  - Interceptar la solicitud de actualización de firmware.
  - Proporcionar un certificado falso junto con un firmware malicioso.
  - El enrutador aceptaría el certificado falso y procedería a instalar el firmware malicioso.
- Contramedidas posibles para mitigar esta vulnerabilidad:
  - Para solucionar esta vulnerabilidad, cualquier router de la marca Asus modelo RT-AC1900P, deberíamos actualizarlo a una versión superior a la 3.0.0.4.385_20253. Actualizar los router no es algo que se haga con frecuencia, pero es muy importante, ya que pueden ocurrir cosas como estas.


### CVE-2021-21819
- Categoría: Servicios de Red Inseguro.
- Descripción: Se presenta una vulnerabilidad de ejecución de código en la funcionalidad de Libcli Test Environment de D-LINK DIR-3040      versión 1.13B03. Una petición de red especialmente diseñada puede conllevar a una ejecución de un comando arbitrario. Un atacante puede   enviar una secuencia de peticiones para activar esta vulnerabilidad.
- Gravedad: 7.2 High.
- Metodo de explotacion: Un atacante podría explotar esta vulnerabilidad de la siguiente manera:
  - Identificar un router D-LINK DIR-3040 vulnerable en la red.
  - Crear una secuencia de peticiones de red maliciosa específicamente diseñadas.
  - Enviar estas peticiones al router a través de la red.
  - Aprovechar la vulnerabilidad en la funcionalidad Libcli Test Environment para ejecutar comandos abiertos.
- Contramedidas posibles para mitigar esta vulnerabilidad:
  - Desactivar servicios innecesarios en el router y usar contraseñas fuertes.
  - Cambiar las credenciales por defecto del router y usar contraseñas fuertes.
  - Considerar el uso de VLANs para aislar dispositivos críticos de la red general.
  - Actualizando el firmware a una versión superior a la 1.13B03.

### CVE-2021-44228
  - Categoría. Ecosistema de interfaces inseguras.
  - Descripción: La vulnerabilidad surge de la forma en que Log4j maneja las solicitudes de registro que contienen referencias a         
  servidores LDAP (Lightweight Directory Access Protocol) y otros endpoints JNDI (Java Naming and Directory Interface). Un atacante 
  puede enviar una solicitud especialmente diseñada que incluye una referencia a un servidor LDAP controlado por el atacante. Cuando 
  Log4j procesa esta solicitud, intenta cargar y ejecutar código desde el servidor LDAP, permitiendo así la ejecución de código 
  arbitrario.
  - Gravedad: 10.0 critical
  - Método de Explotación.
    -  El atacante envía una solicitud de registro especialmente diseñada que contiene una referencia a un servidor LDAP (Lightweight   
    Directory Access Protocol) controlado por el atacante. Esta solicitud se envía a una aplicación que utiliza la biblioteca Log4j para 
    el registro de eventos.
    -  Cuando Log4j procesa la solicitud, intenta resolver la referencia LDAP. Esto hace que la aplicación se conecte al servidor LDAP 
    del atacante y descargue un objeto Java malicioso.
    -  El objeto Java malicioso se ejecuta en el servidor vulnerable, permitiendo al atacante ejecutar código arbitrario. Esto puede 
    llevar a la toma de control completa del sistema afectado, permitiendo al atacante realizar acciones como robar datos, instalar 
    malware o lanzar ataques adicionales.
  - Contramedidas posibles para mitigar esta vulnerabilidad:
    - Es crucial actualizar a una versión no vulnerable de Log4j (2.15.0 o posterior), donde esta funcionalidad ha sido deshabilitada por defecto. Además, se recomienda revisar y actualizar las configuraciones de seguridad para protegerse contra futuras vulnerabilidades.

### CVE-2021-3711
- Categoría. Transferencia y almacenamiento de datos inseguros.
- Descripción. Heartbleed permite a un atacante remoto enviar solicitudes maliciosas a un servidor vulnerable, haciendo que el servidor envíe fragmentos de memoria (hasta 64KB) a la solicitud. Esto puede incluir información sensible como nombres de usuario, contraseñas, claves de cifrado y otros datos confidenciales. La vulnerabilidad surge de un error en la implementación del comando "Heartbeat" en OpenSSL, que permite a los servidores verificar que las conexiones TLS siguen activas.
- Gravedad. 9.8 Critical
- Método de explotación.
  -  El atacante envía una solicitud "heartbeat" especialmente diseñada al servidor. Esta solicitud incluye un tamaño de datos mayor al 
  real.
  -  Debido a la vulnerabilidad, el servidor responde con más datos de los que debería, incluyendo fragmentos de su memoria.
  -  Los datos devueltos pueden contener información sensible como nombres de usuario, contraseñas, claves de cifrado y otros datos 
  confidenciales.
  -  El atacante puede repetir este proceso varias veces para extraer más datos de la memoria del servidor.
- Contramedidas posibles para mitigar esta vulnerabilidad:
  - Es crucial actualizar OpenSSL a una versión no vulnerable (a partir de la versión 1.0.1g) y reemplazar las claves de cifrado y 
  certificados afectados. Además, se recomienda realizar auditorías de seguridad y monitorear las comunicaciones para detectar cualquier 
  actividad sospechosa.

### CVE-2023-6324
- Categoría. Ecosistema de interfaces inseguras.
- Descripción. Es una vulnerabilidad crítica en el ThroughTek Kalay SDK, una plataforma utilizada para la comunicación segura entre dispositivos IoT. Esta vulnerabilidad se debe a que el SDK utiliza un valor PSK (Pre-Shared Key) predecible en la sesión DTLS (Datagram Transport Layer Security) cuando se encuentra con una identidad PSK inesperada.
- Gravedad. 8.1 High
- Método de explotación.
  - El atacante identifica un dispositivo IoT que utiliza el ThroughTek Kalay SDK y que está configurado para usar una identidad PSK 
  (Pre-Shared Key) predecible.
  - El atacante intercepta la comunicación entre el dispositivo IoT y el servidor utilizando técnicas de ataque de intermediario     
  (Man-in-the-Middle).
  - Debido a la vulnerabilidad, el SDK utiliza un valor PSK predecible cuando se encuentra con una identidad PSK inesperada. El atacante 
  aprovecha esta debilidad para establecer una sesión DTLS (Datagram Transport Layer Security) con el dispositivo.
  - Una vez establecida la sesión, el atacante puede acceder a la comunicación entre el dispositivo IoT y el servidor, permitiendo la 
  interceptación y manipulación de datos sensibles transmitidos entre los dispositivos.
- Contramedidas posibles para mitigar esta vulnerabilidad:
  - Es crucial actualizar a una versión no vulnerable del ThroughTek Kalay SDK y asegurarse de que las configuraciones de seguridad 
  estén correctamente implementadas para protegerse contra futuras vulnerabilidades.

<br><br> 
# Clasificación y análisis
## Gravedad
En este apartado, se analiza la gravedad de las vulnerabilidades en función de su impacto potencial sobre la confidencialidad, integridad y disponibilidad de los datos o sistemas. La siguiente tabla presenta una clasificación de los CVEs según su nivel de riesgo:

|   **_CVEs_**   | **_GRAVEDAD_** |
|:--------------:|:--------------:|
| CVE-2021-44228 |      10.0      |
|  CVE-2021-3711 |       9.8      |
|  CVE-2023-6324 |       8.1      |
| CVE-2021-21819 |       7.2      |
| CVE-2020-15498 |       5.9      |

La siguiente tabla muestra la clasificación de las categorías en orden descendente según su nivel de gravedad:

|                  **_CATEGORÍAS_**                 	|
|:-------------------------------------------------:	|
| Transferencia y almacenamiento de datos inseguros 	|
|  Ausencia de un mecanismo de actualización seguro 	|
|   Uso de componentes inseguros o desactualizados  	|
|   Contraseñas débiles, adivinables o codificadas  	|
|             Servicios de red inseguros            	|
|       Configuraciones por defecto inseguras       	|
|         Ecosistema de interfaces inseguras        	|
|            Ausencia de seguridad física           	|
|        Ausencia de gestión de dispositivos        	|
|      Insuficiente protección a la privacidad      	|

<br>

## Facilidad de explotación
A continuación se evaluará la facilidad de explotación de las vulnerabilidades identificadas, considerando qué tan accesibles son para un atacante. La siguiente tabla ofrece una clasificación de estas vulnerabilidades según su nivel de facilidad de explotación:

|   **_CVEs_**   	|
|:--------------:	|
| CVE-2021-44228 	|
| CVE-2020-15498 	|
| CVE-2021-3711  	|
| CVE-2021-21819 	|
| CVE-2023-6324  	|

Esta tabla muestra el orden descendente de las categorías según su facilidad de explotación:

|                  **_Categorías_**                 	|
|:-------------------------------------------------:	|
|   Contraseñas débiles, adivinables o codificadas  	|
|       Configuraciones por defecto inseguras       	|
| Transferencia y almacenamiento de datos inseguros 	|
|   Uso de componentes inseguros o desactualizados  	|
|             Servicios de red inseguros            	|
|  Ausencia de un mecanismo de actualización seguro 	|
|         Ecosistema de interfaces inseguras        	|
|      Insuficiente protección a la privacidad      	|
|        Ausencia de gestión de dispositivos        	|
|            Ausencia de seguridad física           	|

<br>

## Relevancia para TrustShield Financial
Seguidamente, se destacan las vulnerabilidades más críticas que afectan directamente la operación y seguridad financiera de TrustShield Financial. La siguiente tabla resume la relevancia de los CVEs escogidos para la empresa, en orden descendente:

|   **_CVEs_**   	|
|:--------------:	|
| CVE-2021-44228 	|
| CVE-2023-6324  	|
| CVE-2021-3711  	|
| CVE-2021-21819 	|
| CVE-2020-15498 	|

En cambio, esta tabla resume la relevancia de las diferentes categorías, en orden descendente:

|                  **_CATEGORÍAS_**                 	|
|:-------------------------------------------------:	|
| Transferencia y almacenamiento de datos inseguros 	|
|   Contraseñas débiles, adivinables o codificadas  	|
|             Servicios de red inseguros            	|
|       Configuraciones por defecto inseguras       	|
|   Uso de componentes inseguros o desactualizados  	|
|         Ecosistema de interfaces inseguras        	|
|  Ausencia de un mecanismo de actualización seguro 	|
|      Insuficiente protección a la privacidad      	|
|        Ausencia de gestión de dispositivos        	|
|            Ausencia de seguridad física           	|


<br><br>
# Propuesta de contramedidas
Las contramedidas correspondientes a cada vulnerabilidad están descritas en el propio informe del CVE, de manera concisa y resumida para facilitar su implementación.

<br><br>
# Conclusión
En conclusión, nuestros hallazgos evidencian una alarmante cantidad de dispositivos IoT vulnerables, lo que subraya la exposición de estos dispositivos a ciberataques. Dado que los dispositivos IoT están cada vez más integrados en nuestra vida cotidiana, resulta imperativo implementar medidas de seguridad robustas, tales como actualizaciones periódicas de firmware y la utilización de contraseñas complejas. Reforzar la seguridad de estos dispositivos no solo protege la privacidad de los usuarios, sino que también previene posibles amenazas a gran escala.

Tal como se refleja en la propuesta de contramedidas, al ser los dispositivos IoT el foco de nuestro análisis, la prioridad debe ser mantenerlos actualizados a la versión más reciente. Esto ayudará a mitigar, o al menos a dificultar, el acceso no autorizado por parte de posibles atacantes a estos dispositivos IoT.
