
# GUÍA DE INSTALACIÓN DCM4CHEE

Autores: 
* Isabella Ariza Cuberos, *email*: isabella.ariza@udea.edu.com
* Lisset Andrea Zea Monsalve, *email*: lisset.zea@udea.edu.com

## Introducción a DCM4CHEE

DCM4CHE es una colección de aplicaciones y utilidades de código abierto para la empresa de atención médica. Estas aplicaciones se han desarrollado en el lenguaje de programación Java para mejorar el rendimiento y la portabilidad, y admiten la implementación en JDK 1.6 y versiones posteriores.

Por su parte, DCM4CHEE es un administrador de imágenes/archivo de imágenes (según IHE ). La aplicación contiene los servicios e interfaces DICOM y HL7 necesarios para proporcionar almacenamiento, recuperación y flujo de trabajo en un entorno sanitario. DCM4CHEE está preempaquetado e implementado dentro del servidor de aplicaciones JBoss. Aprovechando muchas funciones de JBoss ( JMS , EJB , Servlet Engine, etc.) y asumiendo el papel de varios actores de IHE en aras de la interoperabilidad, la aplicación proporciona muchos servicios robustos y escalables:

|Servicio|Descripción|
|--------|--------|
|Interfaz de usuario basada en web|DCM4CHEE contiene una sólida interfaz de usuario para administradores que se ejecuta completamente en un navegador web.|
|Almacenamiento DICOM|Actuando como un archivo, dcm4chee puede almacenar cualquier tipo de objeto DICOM en sistemas de archivos estándar, con compresión si es necesario.|
|Consulta/Recuperación DICOM|Consulte el archivo de objetos DICOM y recupérelos.|
|WADO y RID|Acceso web al contenido archivado.|
|Otros servicios DICOM|MPPS , GPWL , MWL , compromiso de almacenamiento, notificación de disponibilidad de instancias, notificación de contenido de estudio, contenido de salida a medios de CD, protocolos colgantes y más.|
|Servidor HL7|Un servidor HL7 integrado que puede actuar sobre tipos de mensajes ADT, ORM y ORU.|
|Servicios IHE|dcm4chee puede existir felizmente en un entorno compatible con IHE mediante la integración con un registro y repositorio XDS / XDSI , actuando como un nodo seguro y proporcionando auditoría compatible.|

## Pasos para instalación de DCM4CHEE

En caso de que su sistema operativo sea Windows: 

Instalar Linux en Windows con WSL 

A continuación, se presenta el paso a paso para instalar la distribución de Linux “Ubuntu” utilizando el Subsistema de Windows para Linux. 

Instalar WSL 

Es posible instalar todo lo que necesita para ejecutar el Subsistema de Windows para Linux (WSL) ingresando este comando en un administrador PowerShell o Símbolo del sistema de Windows y luego reiniciando su máquina. 
```
wsl --install 
```

Este comando habilitará los componentes opcionales requeridos, descargará el kernel de Linux más reciente, establecerá WSL 2 como predeterminado e instalará una distribución de Linux en este caso Ubuntu (Predeterminado).
