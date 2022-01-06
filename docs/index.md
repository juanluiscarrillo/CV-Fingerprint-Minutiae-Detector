# Visión Artificial: Fingerprint minutiae detector

Aplicación de visión artificial para detectar minucias en las huellas dactilares. Concretamente, detecta dos tipos de minucias:
- Bifurcaciones
- Terminaciones

Tradicionalmente, las huellas dactilares han servido para la identificación de las personas. Muchos sistemas de visión artificial se basan en la detección de las minucias de las huellas, a partir de las cuales se puede calcular parámetros biométricos con los que determinar si la huella pertenece a un sujeto de la base de datos.

En este trabajo, la detección de las minucias se realiza con técnicas clásicas de Visión Artificial. Además, se cuenta con un programa para generar el *groundtruth* manual de una huella, y otro para comparar la detección realizada con el *ground truth*. Es importante hacer notar, que antes de utilizar estos *scripts* se tiene que haber realizado la detección de la huella.

A continuación, se desarrolla la explicación del trabajo.

## Introducción

Esta aplicación se crea para la asignatura de *Biometría* del Máster de Visión Artificial de la Universidad Rey Juan Carlos de Madrid. Concrétamente, tiene que detectar dos tipos de minucias, bifurcaciones y terminaciones, en imágenes de huellas dactilares. Junto con el código fuente se deja en el repositorio algunas imágenes que pueden ser utilizadas como ejemplo.


## Diseño de la aplicación

La clasificación se realiza con técnicas clásicas de visión artificial: Filtros, erosiones, dilataciones, cierres, aperturas, umbralizado,... 


## Resultados

Los resultados presentan una gran variación en función de la calidad de la imagen de la huella. 


### Utilización de la aplicación

La explicación presupone que se está utilizando linux. No obstante, para otras sistemas operativos los pasos serán similares. Además, se cuenta con que se tienen correctamente instalados: *git*, *python3* y *pip*.

En el repositorio se guardan los ficheros fuentes y las imágenes, por lo que es necesario realizar una serie de pasos para poner en funcionamiento la aplicación. A continuación, se detallan todos los pasos que se ha de seguir:
1. Clonación del proyecto: `git clone https://github.com/juanluiscarrillo/CV-Fingerprint-Minutiae-Detector.git`
2. Acceso a la carpeta del proyecto: `cd CV-Fingerprint-Minutiae-Detector/`
3. Creación de un entorno *venv*: `python3 -m venv ./venv`
4. Activación del entorno: `source ./venv/bin/activate`
5. Instalación de dependencias: `pip3 install -r requirements.txt` 
6. Detección de las minucias: `python Fingerprint.py *img_file*`



También, es posible valorar la tasa de acierto de la aplicación sobre el conjunto de imágenes de test. Para ello habría que ejecutar: `python MelanomaTrainer.py`. 


