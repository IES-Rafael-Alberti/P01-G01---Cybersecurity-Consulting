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

- Contraseñas Débiles, Adivinables o codificadas.
  - Fáciles de adivinar o que, por defecto, permiten acceder a la configuración del dispositivo.
- Servicios de Red Inseguro.
  - Algunos dispositivos cuentan con servicios de red sin las medidas de seguridad adecuadas o tienen servicios innecesarios que solo los   hacen más vulnerables
- Ecosistema de interfaces inseguras.
  - Ocurre cuándo la vulnerabilidad no está en el dispositivo, sino en las aplicaciones que lo administran (ej. un reloj que se conecta a   una app insegura en el teléfono móvil).
- Ausencia de un mecanismo de actualización seguro.
  - Cuándo no se cuentan con mecanismos para realizar una actualización o no son seguros.
- Uso de componentes inseguros o desactualizados.
  - Corresponde al software o hardware con vulnerabilidades y que son utilizados en los dispositivos.
- Insuficiente protección a la privacidad.
  - Algunos dispositivos no cuentan con mecanismos suficientes para proteger y resguardar la información personal y     
    confidencial que se guarda, procesa o transmite por el dispositivo.
- Transferencia y almacenamiento de datos inseguros.
  - Los dispositivos no cuentan con mecanismos para encriptar los datos.
- Ausencia de gestión de dispositivos.
  - Una vulnerabilidad de gestión en dónde los usuarios y empresas desconocen la cantidad de dispositivos que se conectan a su red y el tipo de información que manejan.
- Configuraciones por defecto inseguras.
  - Cuándo las configuraciones que vienen en el dispositivo por parte del fabricante son inseguras.
- Ausencia de seguridad física.
  - Cuándo se pueden hacer cambios físicos al dispositivo y explotar vulnerabilidades.

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
