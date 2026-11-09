# Conceptos Técnicos

## 📋 Índice

1. [A](#a)
2. [B](#b)
3. [C](#c)
4. [D](#d)
5. [E](#e)
6. [F](#f)
7. [G](#g)
8. [H](#h)
9. [I](#i)
10. [J](#j)
11. [K](#k)
12. [L](#l)
13. [M](#m)
14. [N](#n)
15. [O](#o)
16. [P](#p)
17. [Q](#q)
18. [R](#r)
19. [S](#s)
20. [T](#t)
21. [U](#u)
22. [V](#v)
23. [W](#w)
24. [X](#x)
25. [Y](#y)
26. [Z](#z)

---

## A

### API (Interfaz de Programación de Aplicaciones)
Conjunto de reglas y protocolos que permite que diferentes aplicaciones se comuniquen entre sí. Una API define los métodos y formatos de datos que las aplicaciones pueden usar para solicitar y intercambiar información. Por ejemplo, una API REST permite acceder a recursos a través de endpoints HTTP.

### Arquitectura en Capas
Patrón de diseño de software que organiza la aplicación en capas horizontales, cada una con responsabilidades específicas. Típicamente incluye: capa de presentación, capa de lógica de negocio y capa de datos. Facilita el mantenimiento y la escalabilidad.

### Autenticación
Proceso de verificar la identidad de un usuario o sistema. Confirma que la persona o aplicación es quien dice ser, generalmente usando credenciales como contraseñas, tokens o certificados. Fundamental para la seguridad de los sistemas.

---

## B

### Backend
Parte del software que se ejecuta en el servidor. Es responsable de la lógica de negocio, procesamiento de datos y comunicación con bases de datos. Los usuarios no interactúan directamente con el backend, pero todo lo que ven en el frontend depende de él.

### Blob Storage
Servicio de almacenamiento de objetos en Azure que permite guardar grandes cantidades de datos no estructurados (imágenes, videos, documentos). Ofrece escalabilidad, durabilidad y acceso desde cualquier lugar a través de HTTP/HTTPS.

### Bot de Telegram
Aplicación automatizada que interactúa con usuarios en Telegram. Puede recibir mensajes, procesarlos y enviar respuestas. Los bots pueden realizar tareas como consultas de información, notificaciones o integración con otros servicios.

---

## C

### C#
Lenguaje de programación orientado a objetos desarrollado por Microsoft. Se ejecuta en .NET Framework o .NET Core. Combina la potencia de C++ con la simplicidad de Visual Basic, con características modernas como LINQ y programación asincrónica.

### CLI (Interfaz de Línea de Comandos)
Interfaz de usuario basada en texto que permite interactuar con programas escribiendo comandos. Por ejemplo, Azure CLI permite gestionar recursos de Azure desde la terminal sin usar el portal gráfico.

### Cloud (Computación en la Nube)
Modelo de entrega de servicios informáticos a través de internet. En lugar de tener infraestructura local, los recursos (servidores, almacenamiento, bases de datos) se alojan en servidores remotos del proveedor. Ejemplo: Microsoft Azure, AWS.

### Componente React
Bloque reutilizable de código en React que representa parte de la interfaz de usuario. Puede ser un componente de clase o una función, y contiene lógica para renderizar y manejar interacciones del usuario.

### Concepto de Lifting State Up
En React, técnica de mover el estado de un componente hijo al componente padre para que múltiples componentes puedan compartir y sincronizar el mismo estado.

### Container (Contenedor)
Unidad ligera y portátil que empaques una aplicación con todas sus dependencias (código, runtime, librerías). Los contenedores aseguran que la aplicación funcione igual en desarrollo, pruebas y producción. Docker es la tecnología más popular.

### Container Registry
Repositorio central para almacenar, gestionar y distribuir imágenes de contenedores. Azure Container Registry permite almacenar imágenes Docker privadas y controlar quién puede acceder a ellas.

---

## D

### Database (Base de Datos)
Sistema organizado para almacenar, recuperar y gestionar datos. Puede ser relacional (SQL Server, PostgreSQL) o no relacional (MongoDB, Cosmos DB). Las bases de datos permiten aplicaciones acceder y modificar datos eficientemente.

### DevOps
Metodología que combina desarrollo de software y operaciones de TI. Enfatiza colaboración, automatización y mejora continua. Busca acortar ciclos de desarrollo, mejorar la calidad y acelerar la entrega de software.

### Docker
Plataforma de containerización que permite empacar aplicaciones en contenedores. Facilita que las aplicaciones se ejecuten de manera consistente en cualquier entorno (local, servidor, cloud).

### DNS (Sistema de Nombres de Dominio)
Sistema que traduce nombres de dominio legibles por humanos (ejemplo.com) en direcciones IP (192.168.1.1). Permite acceder a servicios web usando nombres fáciles de recordar en lugar de números.

---

## E

### Enrutamiento
En networking, proceso de dirigir paquetes de datos desde su origen a su destino a través de la red. En aplicaciones web, es el mecanismo que mapea URLs a controladores o funciones específicas.

### Escalabilidad
Capacidad de un sistema para crecer y manejar más carga. Puede ser escalabilidad horizontal (agregar más máquinas) o vertical (agregar más recursos a una máquina).

### ExpressRoute
Servicio de Azure que proporciona conexión privada dedicada desde tu centro de datos o red local a Azure. Ofrece mayor ancho de banda, menor latencia y más seguridad que una conexión VPN tradicional.

---

## F

### Firewall
Dispositivo o software de seguridad que monitorea y controla el tráfico de red. Utiliza reglas predefinidas para permitir o bloquear paquetes de datos. Fundamental para proteger redes contra accesos no autorizados. Azure Firewall es el equivalente en la nube.

### Framework
Estructura de código preescrito que proporciona funcionalidad base y patrones para desarrollar aplicaciones. Ejemplos: React, Angular, .NET Framework. Acelera el desarrollo reutilizando código probado.

---

## G

### GitHub
Plataforma web para alojar repositorios Git. Facilita la colaboración entre desarrolladores, permite control de versiones, revisión de código y automatización de flujos de trabajo. Propiedad de Microsoft.

### Git
Sistema de control de versiones distribuido que rastrea cambios en archivos y código. Permite colaboración entre desarrolladores, mantenimiento de histórico y reversión de cambios.

### Gitflow
Modelo de branching para Git que establece un flujo de trabajo con ramas específicas (master, develop, feature, release, hotfix). Facilita la gestión de versiones y lanzamientos en equipo.

---

## H

### Hook en React
Función especial en React que permite usar características de estado y ciclo de vida en componentes funcionales. Ejemplos: useState, useEffect. Los hooks facilitan la reutilización de lógica entre componentes.

### HTTP (Protocolo de Transferencia de Hipertexto)
Protocolo de aplicación usado para transferir datos en la web. Basado en cliente-servidor, define métodos como GET (obtener), POST (enviar), PUT (actualizar) y DELETE (eliminar).

---

## I

### Infraestructura como Código (IaC)
Práctica de describir y gestionar infraestructura (servidores, redes, almacenamiento) usando código. Permite versionar, automatizar y reproducir entornos. Herramientas: Terraform, ARM Templates, Pulumi.

### Instancia de Contenedor
Máquina virtual ligera que ejecuta un contenedor Docker. Azure Container Instances permite ejecutar contenedores sin gestionar servidores. Se paga solo por lo que se usa.

---

## J

### JavaScript
Lenguaje de programación interpretado que se ejecuta en navegadores web. Permite agregar interactividad a páginas web. También se puede ejecutar en servidores (Node.js). Es el lenguaje base del desarrollo web moderno.

### JSON (Notación de Objetos de JavaScript)
Formato ligero para intercambio de datos basado en texto. Fácil de leer para humanos y máquinas. Usado ampliamente en APIs REST para enviar y recibir datos. Estructura: objetos {} y arrays [].

### JSX
Extensión de sintaxis de JavaScript que permite escribir HTML dentro de código JavaScript. Utilizada en React para describir la estructura de componentes de manera declarativa.

---

## K

### Kubernetes
Orquestador de contenedores que automatiza el despliegue, escalado y gestión de contenedores. Distribuye contenedores entre múltiples nodos, maneja fallos y permite actualizaciones sin tiempo de inactividad.

### KQL (Kusto Query Language)
Lenguaje de consulta usado en Azure Data Explorer y Azure Monitor. Permite analizar grandes volúmenes de datos de registros rápidamente.

---

## L

### Linting
Análisis automático de código para detectar errores, violaciones de estilo y problemas potenciales. Herramientas como ESLint (JavaScript) o Pylint (Python) ayudan a mantener código limpio y consistente.

### LINQ (Language Integrated Query)
Característica de .NET que permite realizar consultas sobre colecciones de datos usando sintaxis similar a SQL. Proporciona métodos como Where, Select, GroupBy para filtrar y transformar datos.

---

## M

### Middleware
Software que actúa como intermediario entre diferentes componentes de una aplicación o entre aplicaciones. En APIs, procesa solicitudes antes de llegar al controlador. Puede autenticar, validar, registrar o transformar datos.

### Microsoft Entra
Servicio de identidad y acceso de Microsoft (anteriormente Azure AD). Gestiona autenticación y autorización, permitiendo que usuarios accedan de manera segura a recursos en la nube y locales.

### MSAL (Biblioteca de Autenticación de Microsoft)
Librería que facilita autenticación y adquisición de tokens en aplicaciones. Soporta múltiples plataformas (Web, escritorio, móvil) y flujos de autenticación (OAuth 2.0, OpenID Connect).

---

## N

### NSG (Grupo de Seguridad de Red)
Firewall virtual en Azure que controla el tráfico de red. Contiene reglas de entrada y salida que permiten o deniegan tráfico basado en protocolo, puertos y direcciones IP.

### NVA (Aplicación Virtual de Red)
Máquina virtual que actúa como dispositivo de red (firewall, proxy, router). Permite control avanzado del tráfico de red y aplicar reglas de seguridad complejas.

---

## O

### Objeto en Programación
Instancia de una clase que contiene datos (propiedades) y comportamiento (métodos). Fundamental en programación orientada a objetos. Ejemplo: un objeto Usuario con propiedades como nombre y edad.

### OpenID Connect
Protocolo de autenticación construido sobre OAuth 2.0. Permite que aplicaciones verifiquen la identidad de usuarios y obtengan información básica de perfil.

---

## P

### Peering de VNet
Conexión directa entre dos redes virtuales de Azure. Permite que recursos en diferentes VNets se comuniquen como si estuvieran en la misma red, sin necesidad de pasar por internet.

### PostMan
Aplicación que facilita desarrollo y prueba de APIs. Permite crear solicitudes HTTP, organizarlas en colecciones, automatizar pruebas y documentar APIs.

### PowerShell
Shell y lenguaje de scripting orientado a objetos de Microsoft. Permite automatizar tareas administrativas y gestión de sistemas. Versión moderna: PowerShell Core (multiplataforma).

### Protocolo
Conjunto de reglas y estándares que definen cómo se comunican sistemas. Ejemplos: HTTP, HTTPS, TCP/IP, SMTP. Aseguran que diferentes sistemas puedan entenderse.

### Python
Lenguaje de programación interpretado, de alto nivel y versátil. Enfatiza legibilidad del código. Popular en ciencia de datos, scripting, automatización y desarrollo web. Comunidad activa.

---

## Q

### Query (Consulta)
Solicitud de datos a una base de datos o servicio. En SQL, un query puede buscar, filtrar, agrupar y transformar datos. En APIs REST, corresponde a parámetros URL que especifican qué datos se desean.

---

## R

### React
Librería JavaScript para construir interfaces de usuario con componentes reutilizables. Utiliza Virtual DOM para optimizar actualizaciones. Desarrollado por Facebook, ahora mantenido por Meta.

### Redux
Librería de gestión de estado para aplicaciones JavaScript. Centraliza el estado de la aplicación en un store global, facilita debugging y sincronización entre componentes.

### RESTful
Arquitectura de web service basada en los principios de REST (Transferencia de Estado Representacional). Usa métodos HTTP estándar (GET, POST, PUT, DELETE) y URLs para representar recursos.

### Rol
En contexto de seguridad, define qué permisos tiene un usuario o aplicación. Ejemplo: Administrador, Lector, Editor. Fundamental para control de acceso y principio de menor privilegio.

---

## S

### Service Endpoint
Punto de acceso de red de un servicio Azure. Permite conectarse a servicios como Storage o SQL Database directamente desde una VNet sin pasar por internet público.

### Seguridad en Capas (Defense in Depth)
Estrategia que implementa múltiples niveles de seguridad. Si un nivel es comprometido, otros aún protegen el sistema. Incluye firewalls, encriptación, autenticación multi-factor.

### SQL (Lenguaje de Consulta Estructurado)
Lenguaje estándar para gestionar y consultar bases de datos relacionales. Permite crear, leer, actualizar y eliminar datos. Ejemplos: SQL Server, PostgreSQL, MySQL.

### SSH (Secure Shell)
Protocolo de red seguro para acceder de manera remota a sistemas. Proporciona conexión encriptada. Alternativa segura a Telnet.

### Subred
Segmento de una red virtual en Azure. Cada subred tiene su propio rango de direcciones IP y puede tener reglas de seguridad diferentes. Permite organizar y aislar recursos.

---

## T

### Token
Cadena de caracteres que representa autenticación o autorización. Después de autenticarse, el servidor emite un token (JWT, OAuth) que el cliente incluye en solicitudes posteriores para demostrar autenticidad.

### Tópico en Azure Service Bus
Canal de comunicación asincrónica que implementa patrón publicador-suscriptor. Un publicador envía mensajes a un tópico, y múltiples suscriptores pueden recibirlos.

### TypeScript
Superconjunto de JavaScript que agrega tipado estático. Se compila a JavaScript. Ayuda a detectar errores en tiempo de compilación y mejora la calidad del código.

---

## U

### URI (Identificador de Recurso Uniforme)
Cadena que identifica de manera única un recurso. Más genérico que URL. Sintaxis: esquema://autoridad/ruta?consulta#fragmento. Ejemplo: https://ejemplo.com/api/usuarios/123

### URL (Localizador de Recursos Uniforme)
Dirección específica de un recurso en la web. Ejemplo: https://www.ejemplo.com/index.html. Es un tipo específico de URI.

---

## V

### Validación de Datos
Proceso de verificar que los datos cumplen con reglas y criterios específicos. Importante para seguridad (evitar inyecciones) y calidad de datos. Puede ser del lado cliente o servidor.

### Variable de Entorno
Valor que se establece en el sistema operativo o contenedor que las aplicaciones pueden leer. Usado para configuración sensible (claves, URLs) sin incluirla en código.

### Virtual Machine (VM)
Servidor informático virtualizado que se ejecuta en hardware físico. Tiene su propio sistema operativo, procesador virtual y memoria. Azure ofrece VMs con diferentes tamaños y configuraciones.

### VNet (Red Virtual de Azure)
Red privada aislada en Azure. Permite conectar recursos de Azure (VMs, bases de datos, aplicaciones) entre sí y con redes locales. Proporciona seguridad y control de tráfico.

### VPN (Red Privada Virtual)
Tecnología que crea una conexión encriptada sobre una red pública (internet). Permite acceder de manera segura a recursos remotos como si estuvieras en la red local.

---

## W

### Webhook
Mecanismo de callback HTTP que permite que una aplicación envíe datos a otra aplicación cuando ocurre un evento. Ejemplo: GitHub puede enviar notificaciones a tu servidor cuando ocurre un push.

### Web Service
Servicio web accesible a través de HTTP/HTTPS que proporciona funcionalidad a clientes. Expone operaciones que otros sistemas pueden llamar. Ejemplos: APIs REST, servicios SOAP.

---

## X

### XML (Lenguaje de Marcado Extensible)
Formato de datos basado en texto que usa etiquetas personalizadas. Similar a HTML pero enfocado en describir datos en lugar de presentación. Usado en algunas APIs antes de JSON.

### XPath
Lenguaje de consulta para buscar y navegar documentos XML. Permite seleccionar nodos específicos de un documento XML usando sintaxis similar a rutas de archivos.

---

## Y

### YAML (YAML Ain't Markup Language)
Formato de serialización de datos legible por humanos. Usado frecuentemente en archivos de configuración (Docker Compose, Kubernetes, CI/CD). Usa indentación para estructura.

---

## Z

### Zero Trust Security
Modelo de seguridad que asume que ningún usuario o dispositivo es confiable de forma predeterminada. Requiere verificación continua de identidad y permisos. Implementado por servicios como Entra ID.

---

## 📚 Recursos Adicionales

- [Glosario de Azure](https://learn.microsoft.com/es-es/azure/azure-glossary-cloud-terminology)
- [MDN Web Docs - Glosario](https://developer.mozilla.org/es/docs/Glossary)
- [DevOps Glossary](https://www.atlassian.com/devops)
- [Cloud Computing Glossary](https://cloud.google.com/docs/glossary)

---

**Última actualización**: 2024
**Autor**: Cousi - CousiBlog
