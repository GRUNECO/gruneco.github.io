# Introducción a EEGLAB
EEGLAB es una colección de funciones de MATLAB que pueden ser llamadas desde una interfaz gráfica principal o a través de comandos de línea [1]. En esta
guía se expondrán diferentes pasos a seguir para pre-procesar los registros de las dos maneras; sin embargo es una información básica que puede ser ampliada en
las referencias mencionadas para cada sección.

El mecanismo de historia de EEGLAB EEG.history guarda todas las operaciones que se han ejecutado en los datasets desde la interfaz gráfica, lo que permite
conocer qué comandos se han utilizado para determinados procesos realizados y construir líneas de código que puedan hacer en gran medida un procesamiento
automático de múltiples señales. De este modo, es importante conocer la estructura de los datos EEG y las subestructuras principales de éstos, como son: EEG.data,
EEG.event, EEG.urevent, EEG.epoch, EEG.chanlocs and EEG.history [1].

EEGLAB utiliza cinco nombres de variables reservadas para su uso :
  * EEG - Actual dataset EEG
  * ALLEEG - Colección de todos los datasets EEG cargados
  * CURRENTSET - El índice de dataset actuales
  * LASTCOM - El último comando utilizado desde el menú EEGLAB
  * ALLCOM - Todos los comandos utilizados desde el menú EEGLAB
 
Se puede acceder a cada una de ellas o a las subestructuras escribiendo en la ventana de comandos de MATLAB el nombre de la variable que desea ser vista [1], por ejemplo:
```>> ALLEEG(1)```

Retorna la estructura del primer dataset cargado en el workspace EEGLAB/MATLAB con toda la información de éste [1].
```>> EEG```

Incluye el nombre del archivo, el número y la locación de los canales, la frecuencia de muestreo de los datos, el número de épocas o ensayos, información acerca de
los eventos, cada una de las épocas, entre otros [2]. Para acceder a un dataset que se ha importado o guardado en ese momento y se desea ver en la interfaz gráfica, se utiliza el siguiente comando >> eeglab redraw. Si
hay abierta una sesión de EEGLAB primero escriba ```>> [ALLEEG EEG CURRENTSET] = eeg_store(ALLEEG, EEG)``` para guardar la información modificada
y luego el comando anterior [1].

## Estructuras de datos de EEGLAB

Sección utilizada para el uso de EEGLAB y el uso de las funciones en los scripts de
MATLAB [1].

La estructura EEG contiene toda la información del dataset actual cargado a EEGLAB. Para ver lo que incluye esta estructura y lo que se ha procesado en el
dataset, se puede proceder en la ventana de comandos de MATLAB con >> EEG y aparecerán las siguientes líneas de comandos (ver figura 1) [2].

**Figura 1**.​ Información del dataset cargado a EEGLAB [2].

## EEGLAB pop_functions 

Las funciones con el prefijo pop_ o eeg_ son funciones que toman la estructura EEG como su primer argumento. Las funciones con el prefijo pop_ pueden ser llamadas ya sea desde el menú de EEGLAB o por un comando de línea, mientras que las funciones con el prefijo eeg_ sólo pueden ser llamadas con un comando de línea de MATLAB. Las funciones pop_ pueden ser llamadas desde el menú de EEGLAB a través de las diferentes secciones y abrirán una ventana para llenar una serie de parámetros y continuar con el procesamiento. Luego aparecerá en el historial de EEG las funciones con los parámetros utilizados para ser generadas desde unas líneas de comandos. Si la función es llamada sólo con el primer parámetro EEG, se abrirá una ventana de consulta interactiva para ser llenada; pero si no se remueven o cambian esos parámetros, el procesamiento se hará directamente (sin abrir ninguna ventana) con las indicaciones dadas anteriormente [1].

Por ejemplo, si se escribe ```>> EEG = pop_eegfilt(EEG)``` en la ventana de comandos, esto abrirá una ventana interactiva permitiendo filtrar los datos de acuerdo a unos parámetros de entrada. Si se desea filtrar el dataset EEG sin una interfaz gráfica se puede escribir por ejemplo >> EEG = pop_eegfilt( EEG, 1, 0), lo cual es un filtro pasa altas que filtrará los datos por encima de 1 Hz [1].

Para ver el estado del dataset actual utilice la función ```>> EEG = eeg_checkset(EEG)```. Ésta también sirve para revisar la estructura del evento y es llamada cada que el dataset es modificado, convirtiendo valores numéricos a cadenas si es necesario [1,3].
