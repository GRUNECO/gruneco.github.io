
# GUÍA DE INSTALACIÓN DCM4CHEE

Autores: 
* Isabella Ariza Cuberos, *email*: isabella.ariza@udea.edu.com
* Lisset Andrea Zea Monsalve, *email*: lisset.zea@udea.edu.com

## Introducción a DCM4CHEE

DCM4CHE es una colección de aplicaciones y utilidades de código abierto para la empresa de atención médica. Estas aplicaciones se han desarrollado en el lenguaje de programación Java para mejorar el rendimiento y la portabilidad, y admiten la implementación en JDK 1.6 y versiones posteriores.

Por su parte, DCM4CHEE es un administrador de imágenes/archivo de imágenes (según IHE ). La aplicación contiene los servicios e interfaces DICOM y HL7 necesarios para proporcionar almacenamiento, recuperación y flujo de trabajo en un entorno sanitario. DCM4CHEE está preempaquetado e implementado dentro del servidor de aplicaciones JBoss. Aprovechando muchas funciones de JBoss ( JMS , EJB , Servlet Engine, etc.) y asumiendo el papel de varios actores de IHE en aras de la interoperabilidad, la aplicación proporciona muchos servicios robustos y escalables [1]:

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

Configure su información de usuario de Linux 

Una vez que haya instalado WSL, deberá crear una cuenta de usuario y una contraseña para su distribución de Linux recién instalada [1]. 

Finalizado este proceso ingrese a la ventada de comandos de Ubuntu y proceda a iniciar la instalación. 

1. **Instalar Docker** 

```
sudo apt-get install docker.io 
```
2. **Agregar grupos ** 
```
sudo -i 
```
3. **Indicar password y luego como root**

```
groupadd -r slapd-dcm4chee --gid=1021 && useradd -r -g slapd-dcm4chee --uid=1021 slapd-dcm4chee 

groupadd -r postgres-dcm4chee --gid=999 && useradd -r -g postgres-dcm4chee --uid=999 postgres-dcm4chee 

groupadd -r dcm4chee-arc --gid=1023 && useradd -r -g dcm4chee-arc --uid=1023 dcm4chee-arc 

groupadd -r keycloak-dcm4chee --gid=1029 && useradd -r -g keycloak-dcm4chee --uid=1029 keycloak-dcm4chee  
```
4. **Cerrar sesión root **
```
Exit 
```

5.** Iniciar Docker **
```
Sudo dockerd 
```
 
6. **Actualizar **
```
Sudo apt-get update 
```
7. **Crear la interfaz de red virtual **
```
sudo docker network create dcm4chee_default 
```
8. **Iniciar la imagen LDAP **
```
sudo docker run --network=dcm4chee_default --name ldap -p 389:389 -v /etc/localtime:/etc/localtime:ro -v /etc/timezone:/etc/timezone:ro -v /var/local/dcm4chee-arc/ldap:/var/lib/ldap -v /var/local/dcm4chee-arc/slapd.d:/etc/ldap/slapd.d -d dcm4che/slapd-dcm4chee:2.4.44-16.0 
```

9.** Iniciar la imagen Keycloak **
```
sudo docker run --network=dcm4chee_default --name keycloak -p 8880:8880 -p 8843:8843 -p 8990:8990 -e HTTP_PORT=8880 -e HTTPS_PORT=8843 -e MANAGEMENT_HTTP_PORT=8990 -e KEYCLOAK_WAIT_FOR=ldap:389 -v /etc/localtime:/etc/localtime:ro -v /etc/timezone:/etc/timezone:ro -v /var/local/dcm4chee-arc/keycloak:/opt/keycloak/standalone -d dcm4che/keycloak:4.6.0-16.0 
```

 
 

## Referencias

[1] "Open Source Clinical Image and Object Management", 2022. [En línea]. Disponible en:
https://www.dcm4che.org/. [Consultado 03- Oct- 2022].

