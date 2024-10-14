# Cybersecurity Consulting

![Portada](https://www.fujitsu.com/es/imagesgig5/consulting-banner_tcm77-6603636_tcm77-6286607-32.jpg)

# ÍNDICE

- Introducción
- Investigación de Vulnerabilidades
  - Fase 1: Categorías
  - Fase 2: Investigación de CVEs
- Clasificación y análisis
- Propuesta de contramedidas
- Conclusión


# INTRODUCCIÓN

Hemos recibido un encargo por parte de la empresa TrustShield Financial, dónde nos ha pedido realizar un análisis de su infraestructura tecnológica. Pretenden que identifiquemos vulnerabilidades críticas que podrían comprometer la confidencialidad, integridad y disponibilidad de los datos financieros. Para ello nos hemos centrado en la categoría de tecnologías IoT ya que estos dispositivos están cada vez más presentes en nuestra vida cotidiana y en entornos industriales, lo que los convierte en un objetivo atractivo para los atacantes. La interconexión de estos dispositivos ofrece numerosas ventajas, como la mejora de la eficiencia operativa y la creación de nuevas oportunidades de negocio. Sin embargo, también introduce riesgos significativos en términos de seguridad.

En nuestra investigación, hemos identificado varias categorías de vulnerabilidades que afectan a los dispositivos IoT. Algunas de las más comunes incluyen:
- Autenticación Débil. 
- Actualizaciones de Firmware Inseguras.
- Comunicación No Cifrada.
- Configuraciones Inseguras.
- Falta de Segmentación de Red.
  
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
- Contramedidas posibles: Para mitigar esta vulnerabilidad:
  - Actualizar el firmware del enrutador ASUS  RT-AC1900P a la versión 3.0.0.4.385_20253 o posterior.

### CVE-2021-21819

- Categoría: Servicios de Red Inseguro.
- Descripción: Se presenta una vulnerabilidad de ejecución de código en la funcionalidad de Libcli Test Environment de D-LINK DIR-3040      versión 1.13B03. Una petición de red especialmente diseñada puede conllevar a una ejecución de un comando arbitrario. Un atacante puede   enviar una secuencia de peticiones para activar esta vulnerabilidad.
- Gravedad: 7.2 High.
- Metodo de explotacion: Un atacante podría explotar esta vulnerabilidad de la siguiente manera:
  - Identificar un router D-LINK DIR-3040 vulnerable en la red.
  - Crear una secuencia de peticiones de red maliciosa específicamente diseñadas.
  - Enviar estas peticiones al router a través de la red.
  - Aprovechar la vulnerabilidad en la funcionalidad Libcli Test Environment para ejecutar comandos abiertos.
- Contramedidas posibles: Para mitigar esta vulnerabilidad:
  - Implementar firewalls y sistemas de detección de intrusiones para monitorear y bloquear tráfico sospechoso.
  - Limitar el acceso a la interfaz de administración del router solo a direcciones IP confiables.
  - Desactivar servicios innecesarios en el router y usar contraseñas fuertes.
  - Cambiar las credenciales por defecto del router y usar contraseñas fuertes.
  - Considerar el uso de VLANs para aislar dispositivos críticos de la red general.

### CVE-2021-44228

  - Categoría. Ecosistema de interfaces inseguras.
  - Descripción: La vulnerabilidad surge de la forma en que Log4j maneja las solicitudes de registro que contienen referencias a servidores LDAP (Lightweight Directory Access Protocol) y otros endpoints JNDI (Java Naming and Directory Interface). Un atacante puede enviar una solicitud especialmente diseñada que incluye una referencia a un servidor LDAP controlado por el atacante. Cuando Log4j procesa esta solicitud, intenta cargar y ejecutar código desde el servidor LDAP, permitiendo así la ejecución de código arbitrario.
  - Gravedad: 10.0 critical
  - Método de Explotación.
    -  El atacante envía una solicitud de registro especialmente diseñada que contiene una referencia a un servidor LDAP (Lightweight Directory Access Protocol) controlado por el atacante. Esta solicitud se envía a una aplicación que utiliza la biblioteca Log4j para el registro de eventos.
    -  Cuando Log4j procesa la solicitud, intenta resolver la referencia LDAP. Esto hace que la aplicación se conecte al servidor LDAP del atacante y descargue un objeto Java malicioso.
    -  El objeto Java malicioso se ejecuta en el servidor vulnerable, permitiendo al atacante ejecutar código arbitrario. Esto puede llevar a la toma de control completa del sistema afectado, permitiendo al atacante realizar acciones como robar datos, instalar malware o lanzar ataques adicionales.
  - Contramedidas posibles.
Es crucial actualizar a una versión no vulnerable de Log4j (2.15.0 o posterior), donde esta funcionalidad ha sido deshabilitada por defecto. Además, se recomienda revisar y actualizar las configuraciones de seguridad para protegerse contra futuras vulnerabilidades.

### CVE-2021-3711
- Categoría. Transferencia y almacenamiento de datos inseguros.
- Descripción. Heartbleed permite a un atacante remoto enviar solicitudes maliciosas a un servidor vulnerable, haciendo que el servidor envíe fragmentos de memoria (hasta 64KB) a la solicitud. Esto puede incluir información sensible como nombres de usuario, contraseñas, claves de cifrado y otros datos confidenciales. La vulnerabilidad surge de un error en la implementación del comando "Heartbeat" en OpenSSL, que permite a los servidores verificar que las conexiones TLS siguen activas.
- Gravedad. 9.8 Critical
- Método de explotación.
  - 1. El atacante envía una solicitud "heartbeat" especialmente diseñada al servidor. Esta solicitud incluye un tamaño de datos mayor al real.
  - 2. Debido a la vulnerabilidad, el servidor responde con más datos de los que debería, incluyendo fragmentos de su memoria.
  - 3. Los datos devueltos pueden contener información sensible como nombres de usuario, contraseñas, claves de cifrado y otros datos confidenciales.
  - 4. El atacante puede repetir este proceso varias veces para extraer más datos de la memoria del servidor.
- Contramedidas posibles.
  - Es crucial actualizar OpenSSL a una versión no vulnerable (a partir de la versión 1.0.1g) y reemplazar las claves de cifrado y certificados afectados. Además, se recomienda realizar auditorías de seguridad y monitorear las comunicaciones para detectar cualquier actividad sospechosa.

### CVE-2023-6324
- Categoría. Ecosistema de interfaces inseguras.
- Descripción. Es una vulnerabilidad crítica en el ThroughTek Kalay SDK, una plataforma utilizada para la comunicación segura entre dispositivos IoT. Esta vulnerabilidad se debe a que el SDK utiliza un valor PSK (Pre-Shared Key) predecible en la sesión DTLS (Datagram Transport Layer Security) cuando se encuentra con una identidad PSK inesperada.
- Gravedad. 8.1 High
- Método de explotación.
  - El atacante identifica un dispositivo IoT que utiliza el ThroughTek Kalay SDK y que está configurado para usar una identidad PSK (Pre-Shared Key) predecible.
  - El atacante intercepta la comunicación entre el dispositivo IoT y el servidor utilizando técnicas de ataque de intermediario (Man-in-the-Middle).
  - Debido a la vulnerabilidad, el SDK utiliza un valor PSK predecible cuando se encuentra con una identidad PSK inesperada. El atacante aprovecha esta debilidad para establecer una sesión DTLS (Datagram Transport Layer Security) con el dispositivo.
  - Una vez establecida la sesión, el atacante puede acceder a la comunicación entre el dispositivo IoT y el servidor, permitiendo la interceptación y manipulación de datos sensibles transmitidos entre los dispositivos.
- Contramedidas posibles.
  - Es crucial actualizar a una versión no vulnerable del ThroughTek Kalay SDK y asegurarse de que las configuraciones de seguridad estén correctamente implementadas para protegerse contra futuras vulnerabilidades.
