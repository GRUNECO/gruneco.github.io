---
title:  "Software EEG"
---

# Flujo de trabajo

## Pasos para el preprocesamiento de datos de EEG

1. Realizar instalación de paquetes sova y armonización que se encuentran alojados en GitHub. Abrir una consola de comandos y ejecute las siguientes líneas de comandos:  

**NOTA:** Si el objetivo es armonizar bases de datos provenientes de varios centros de referencia, adquiridos por distintos dispositivos, con una frecuencia de muestreo y canales diferentes, se debe realizar el procesamiento desde el paquete sovaharmony de lo contrario se puede realizar el procesamiento únicamente tomando el paquete sovaflow. Sin embargo, se recomienda utilizar sovaharmony que tiene incorporado tanto la rutina de preprocesamiento como la de post-procesamiento. 

2. Verificar instalación de las librerías y las versiones de los paquetes previamente instalados.  

3. Ejecutar rutina de procesamiento, que se encuentra en el repositorio eeg_harmonization, en el archivo de Python *processingEEG.py*

![Procesamiento](img\paths_prop.png)

4. Ejecutar rutina de calidad 

5. Evaluar resultados 

# Descripción de paquetes del flujo de preprocesamiento

## Python

- [Sovawica](https://gruneco.github.io/sovawica.html)
- [Sovareject](https://gruneco.github.io/sovareject.html)
- [Sovaflow](https://gruneco.github.io/sovaflow.html)
- [Sovachronux](https://gruneco.github.io/sovachronux.html)
- [Sovaviolin](https://gruneco.github.io/sovaviolin.html)
- [Sovaharmony](https://gruneco.github.io/sovaharmony.html)
- [Sovabids](https://gruneco.github.io/sovabids.html)

## Matlab

- [EEGLAB](https://gruneco.github.io/eeglab.html)
- [GUÍA DE IMPORTACIÓN EDF](https://gruneco.github.ioguidelines_import_edf.html)













