---
title:  "Software EEG"
---

# Flujo de trabajo

## Pasos para el preprocesamiento de datos de EEG

1. Realizar instalación de paquetes sova y armonización que se encuentran alojados en GitHub. Abrir una consola de comandos y ejecute las siguientes líneas de comandos:  
```
​# Installation package sovaflow 

​pip install git+https: // gitfront.io/r/GRUNECO/xiGpXFpQvM2T/sovaflow.git 

​# Installation package sovareject 

​pip install git+https: //gitfront.io/r/yjmantilla/5c5817890b14af2e5ae8ae9ba3f14522c337522e/sovareject.git 

​# Installation package sovachronux 

​pip install git+https: //gitfront.io/r/GRUNECO/5wAdEXRh7oTf/sovachronux.git 

​# Installation package eeg_harmonization 

​git clone git+https: https://github.com/GRUNECO/eeg_harmonization.git 

​cd eeg_harmonization 

​pip install -r requirements-install.txt
```
**NOTA:** Si el objetivo es armonizar bases de datos provenientes de varios centros de referencia, adquiridos por distintos dispositivos, con una frecuencia de muestreo y canales diferentes, se debe realizar el procesamiento desde el paquete sovaharmony de lo contrario se puede realizar el procesamiento únicamente tomando el paquete sovaflow. Sin embargo, se recomienda utilizar sovaharmony que tiene incorporado tanto la rutina de preprocesamiento como la de post-procesamiento. 

2. Verificar instalación de las librerías y las versiones de los paquetes previamente instalados.  

3. Ejecutar rutina de procesamiento, que se encuentra en el repositorio eeg_harmonization, en el archivo de Python *processingEEG.py*

![Procesamiento](img\paths_prop.png)

4. Ejecutar rutina de calidad 

5. Evaluar resultados 

# Descripción de paquetes del flujo de preprocesamiento

- [Sovawica](https://gruneco.github.io/sovawica.html)
- [Sovareject](https://gruneco.github.io/sovareject.html)
- [Sovaflow](https://gruneco.github.io/sovaflow.html)
- [Sovachronux](https://gruneco.github.io/sovachronux.html)
- [Sovaviolin](https://gruneco.github.io/sovaviolin.html)
- [Sovaharmony](https://gruneco.github.io/sovaharmony.html)
- [Sovabids](https://gruneco.github.io/sovabids.html)













