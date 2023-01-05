# GUÍA DE IMPORTACIÓN EDF

**Autores**: 
* Carolina Serna, *email*: carolinasernarojas@gmail.com
* Francisco García, *email*: fpretelt@gmail.com

**Año**: 2017 

El formato de datos europeo (EDF por sus siglas en inglés) es un formato simple y sencillo para guardar e intercambiar señales biológicas y físicas multicanal. Además existe una extensión de EDF llamada EDF+. Los lectores son compatibles para ambos archivos, la diferencia es que EDF+ puede contener grabaciones interrumpidas, anotaciones, estímulos y eventos [1].

La importación de EDF o EDF+ se puede realizar con la librería ReadSaveEDF elaborada por Andrey Shapkin en 2012 [2], o con la librería edfread elaborada por Brett Shoelson en 2011 [3] que se encuentran dentro de la carpeta Importación EDF. Sin embargo, el código ha sido probado para EDF+ por lo que no se garantizan resultados con EDF.

Para realizar el paso de los datos en formato EDF+ a Set, formato utilizado por EEGLAB, se puede hacer uso de alguno de los siguientes códigos encontrados dentro de la misma carpeta:
    - import_EDF.m: para un solo archivo.
    - import_EDF_folder.m: para varios archivos.
    - import_EDF_folder_Linux.m: para varios archivos utilizando Linux.
  
A continuación se explica la importación de .edf hasta .set de EEGLAB con el código import_EDF_folder.m (los otros códigos funcionan de manera similar) y utilizando como ejemplo la base de datos de PhysioNet para imaginación y movimiento motor, encontrados en la carpeta Dataset EGG Motor movement/Imagery.

Importación desde EDF+ con el código ​import_EDF_folder.m. El script de importación desde EDF+ está diseñado para leer una carpeta madre que contenga n subcarpetas asociadas a distintos sujetos (1,2,3,..,m), dentro de las cuales se encuentran los archivos .edf a convertir, como se muestra en la figura 1.

<center>
<b>Figura 1.</b>​ Método de importación desde EDF
</center>

El script creará una carpeta llamada “registros_set” dentro de cada subcarpeta asociada a cada sujeto, en la cual guardará los archivos .set importados,correspondientes al respectivo sujeto.

<center>
<b>Figura 2</b>.​ PATH, dirección de la carpeta madre.
</center>

La figura 2 muestra el lugar (recuadro azul) en el cual debe colocarse la dirección asociada a la carpeta madre, ésta debe contener las respectivas subcarpetas correspondientes a cada sujeto.

En el código se encuentra la descripción de cada paso que se realiza para la importación de los archivos EEG .edf a .set. Para conocer más información acerca de la importación de estos archivos a EEGLAB se puede revisar la guía de esta herramienta.

Para cargar los datos de la localización de los canales de cada dataset observe la figura 3.

Figura 3.​ Ruta correspondiente al archivo de locación de canales.

En la figura 3 (recuadro azul) se muestra el lugar en el cual se debe ingresar la dirección correspondiente al archivo .ced, que contiene la ubicación de los canales del registro. Para este caso se muestra como ejemplo la base de datos de PhysioNet para imaginación y movimiento motor.

El último paso de este script es la unión de varios registros de acuerdo a la tarea que desempeñan, que puede ser útil para la base de datos mencionada.

## Consideraciones:

➢ La importación de registros .edf directamente desde EEGLAB, se puede
realizar, pero se debe tener cuidado en la importación de los eventos y los
estímulos presentes en el paradigma, ya que se ha observado que no se
importan de manera correcta.

➢ También se puede realizar la visualización con EDFbrowser prestando
atención a los tiempos y de igual forma a los eventos presentes en el registro.

## Referencias

[1] B. Kemp, "European Data Format (EDF)", Edfplus.info. [En línea]. Disponible en: http://www.edfplus.info/. [Consultado: 07- Sep- 2016].

[2] A. Shapkin, "File Exchange - MATLAB Central", Mathworks.com, 2013. [En
línea]. Disponible en:https://www.mathworks.com/matlabcentral/fileexchange/38641-reading-and-saving-of-data-in-the-edf+/all_files. [Consultado: 10- Sep- 2016].

[3] B. Shoelson, "edfRead - File Exchange - MATLAB Central", Mathworks.com,
2016. [En línea]. Disponible en: https://www.mathworks.com/matlabcentral/fileexchange/31900-edfread. [Consultado:10- Sep- 2016].