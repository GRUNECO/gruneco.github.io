
# SOVABIDS

<p style="text-align: justify;">

Paquete de Python 

Software para la conversion de datos eeg al formato bids [documentación](sovabids.readthedocs.io)

## Estandarización BIDS 
Descargar y reubicar la base de datos 

Evaluar la disponibilidad y distribución de la información y el formato (Verificar si está en formato BIDS o si tiene la información necesaria para realizar la conversión a BIDS). Si no se encuentra en formato BIDS, realizar la conversión de los datos utilizando SOVABIDS, utilizando la documentación: https://sovabids.readthedocs.io/en/latest/  

**Test BIDS** 

Permite identificar si una base de datos se encuentra en formato BIDS. Para realizar esta prueba diríjase al siguiente repositorio de GitHub: <https://github.com/GRUNECO/eeg_harmonization> y en la carpeta Carpeta abierta 📁 misc, ejecute el archivo *pybids_test.py*. 

![Ruta pybids](img\path_pybids.png)

Para la ejecución del archivo *pybids_test.py*, modifique la variable **path** con la ruta de la base de datos que busca evaluar, especifique la **extensión** del archivo que contiene la información EEG y si la base de datos incluye diferentes tareas o estados coloque el indicativo correspondiente en el parámetro ‘task’. La cantidad de líneas que definen la variable **eegs** corresponde a la cantidad de condiciones o tareas en la base de datos.  

**Ejemplo:** Si la base de datos contiene reposo en ojos abiertos (OE) y ojos cerrados (CE), el archivo contendrá 2 líneas de código asignadas a **eegs**. 

1. Si la base de datos está en formato BIDS el resultado de correr el código sería: **BIDS format OK** 

2. Si la base de datos no está en formato BIDS el resultado de correr el código sería: 
**Try to convert of Dataset in BIDS format using "conversion_bids"**

3. En caso de que el resultado sea el presentado en la opción 2 utilizar el siguiente recurso:  

|Recurso|Descripción|Ubicación GITHUB|Método de uso|
|--------|--------|--------|--------|
|SOVABIDS|Software de conversión de EEG a BIDS centrado en la automatización, la reproducibilidad y la interoperabilidad de los datos.  |https://github.com/yjmantilla/sovabids|<p>Realizar la instalación de sovabids por medio de la consola:<br> ```git clone https://github.com/yjmantilla/sovabids.git cd sovabids pip install -r requerements-user.txt```<br> **Observación:** Todos los sujetos se deben encontrar en la misma carpeta 📁</p>|

<https://github.com/GRUNECO/eeg_harmonization/blob/main/misc/conversion_bids.py>

Abrir el archivo conversión_bids.py editar las variables: 

- **source_path**: Ruta de base de datos sin formato BIDS a convertir 

- **bids_path**: Ruta final donde se almacenará la base de datos en formato BIDS 

- **rules_path**: Ruta del archivo de reglas que se explica a continuación 


![Paths BIDS](img\paths_bids.png)

Una vez se tienen las rutas y el archivo de reglas, únicamente se deber ejecutar el código y esperar a que finalice la conversión. 

<https://github.com/GRUNECO/eeg_harmonization/blob/main/misc/reglasLEMON.yml> 

Tomar de base un archivo.yml como el que se presenta en el respositorio de Github y editar cada parámetro como se explica en la documentación del archivo: 

- task: hace referencia al tipo de tarea o condición 
- Name: nombre de la base de datos 
- Authors: Autores de la base de datos 
- PowerLineFrequency: Se realiza el grafico del espectro para evidenciar por inspección visual la frecuencia 
- EEGReference: Canal de referencia 
- Channels: Información de los canales 
- eeg_extension: extensión del archivo EEG  
- pattern: estructura del nombre del archivo de EEG 

Si el archivo tiene una estructura compleja debido a la cantidad de tareas, condiciones, sesiones, etc. Es necesario crear un parámetro adicional: 

fields: especifica cada uno de los elementos que diferencias los registros dentro de la base de datos.  

**Ejemplo:**
```  
pattern : Codificado_EEG_V0_V1_V2_V3\/(.+)\/(.+_.{3})_(.+)_(.+).cnt # For example here we extract from the path the "subject" child of the "entities" object 

fields : 

 - entities.session 

 - entities.subject 

 - ignore 

 - entities.task 
```  
Una vez realizada la conversión y verificación del dataset a utilizar se procede a la instalación del paquete de preprocesamiento SOVA. 
 
</p>

