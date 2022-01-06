# Visión Artificial: Fingerprint minutiae detector

Aplicación de visión artificial para detectar minucias en las huellas dactilares. Concretamente, detecta dos tipos de minucias:
- Bifurcaciones
- Terminaciones

Tradicionalmente, las huellas dactilares han servido para la identificación de las personas. Muchos sistemas de visión artificial se basan en la detección de las minucias de las huellas, a partir de las cuales se pueden calcular parámetros biométricos con los que determinar si la huella pertenece a un sujeto de la base de datos.

En este trabajo, la detección de las minucias se realiza con técnicas clásicas de Visión Artificial. Además, se cuenta con un programa para generar el *ground truth* manual de una huella, y otro para comparar la detección realizada con el *ground truth*. Es importante hacer notar, que antes de utilizar estos últimos *scripts*, se tiene que haber realizado la detección de la huella.

A continuación, se desarrolla la explicación del trabajo.

## Introducción

Esta aplicación se crea para la asignatura de Biometría del Máster de Visión Artificial de la Universidad Rey Juan Carlos de Madrid. Concrétamente, tiene que detectar dos tipos de minucias, bifurcaciones y terminaciones, en imágenes de huellas dactilares. Junto con el código fuente, se deja en el repositorio algunas imágenes que pueden ser utilizadas como ejemplo.


## Diseño de la aplicación

La clasificación se realiza con técnicas clásicas de visión artificial: Filtros, erosiones, dilataciones, cierres, aperturas, umbralizado,... La aplicación genera una imagen donde se muestra el resultado de la detección. La sección de la imagen que se tiene en cuenta para la generación de las minucias aparece delimitada por un cuadrado naranja. Con pequeños cuadrados rojos se muestran las minucias de terminación, mientras que las de bifurcación se muestran con pequeños cuadrados verdes.



### Utilización de la aplicación

La explicación presupone que se está utilizando linux. No obstante, para otros sistemas operativos los pasos serán similares. Además, se cuenta con que se tienen correctamente instalados: *git*, *python* y *pip*.

En el repositorio se guardan los ficheros fuentes y las imágenes, por lo que es necesario realizar una serie de pasos para poner en funcionamiento la aplicación. A continuación, se detallan todos los pasos que se ha de seguir:
1. Clonación del proyecto: `git clone https://github.com/juanluiscarrillo/CV-Fingerprint-Minutiae-Detector.git`
2. Acceso a la carpeta del proyecto: `cd CV-Fingerprint-Minutiae-Detector/`
3. Creación de un entorno *venv*: `python3 -m venv ./venv`
4. Activación del entorno: `source ./venv/bin/activate`
5. Instalación de dependencias: `pip3 install -r requirements.txt` 
6. Detección de las minucias: `python Fingerprint.py [-i INPUT]`. Siendo *INPUT* la ruta del fichero que contiene la imagen de la huella que se quiere detectar. Si no se indica ningún parámetro en la llamada, por defecto se detecta una de las huellas que acompañan al proyecto.

Una vez realizada la detección de un huella, si se quiere lanzar la aplicación que crea el *ground truth*, hay que utilizar el siguiente comando: `python FingerprintGroundTruth.py [-i INPUT] [-e]`. Donde, de nuevo, *INPUT* es la ruta de la imagen. Si no se utiliza parámetro *-i INPUT* la detección se realiza con la imagen por defecto. Además, con el parámetro *-e* es posible editar un *ground truth* creado previamente. 

La aplicación genera el mismo cuadrado naranja sobre el que indicar las minucias. Pulsando con el botón izquierdo del ratón dentro de este cuadrado, se crean las minucias de terminación. Las de bifurcación se crean pulsando con el botón central del ratón. Los datos se guardan pulsando la tecla *s*.

Para borrar minucias, hay que entrar al modo de borrado, pulsando la tecla *d*. En este modo, pulsando sobre el centro de la minucia, ésta desaparece. Para salir del modo de borrado, hay que volver a pulsar la tecla *d*.

Una vez que se ha creado el *ground truth* se puede comprobar visualmente el desempeño de la apliación. Para ello, hay que utilizar el siguiente comando: `python FingerprintEvaluation.py [-i INPUT] [-d DIST]`. Lo comentado anteriormente, también se aplica aquí  para el parámetro *-i INPUT*. Con el parámetro *-d DIST* se indica la distancia máxima admisible en píxeles para considerar válida la minucia detectada frente a la del *ground truth*. Si no se utiliza este parámetro, por defecto toma el valor de 8 píxeles.

La aplicación muestra dos imágenes:
- Detección -> El color de los cuadraditos indica:
    - Rojo: Minucia de terminación correctamente detectada, según el *ground truth*
    - Verde: Minucia de bifurcación correctamente detectada, según el *ground truth*
    - Violeta: Minucia de terminación erróneamente detectada, según el *ground truth*
    - Azul: Minucia de bifurcación erróneamente detectada, según el *ground truth*
- *Ground truth* -> El color de los cuadraditos indica:
    - Rojo: Minucia de terminación del *ground truth* que se ha detectado correctamente
    - Verde: Minucia de bifurcación del *ground truth* que se ha detectado correctamente
    - Violeta: Minucia de terminación del *ground truth* que no se ha detectado
    - Azul: Minucia de bifurcación del *ground truth* que no se ha detectado

NOTA: Si se ha detectado una minucia, pero no coincide con el tipo, se la considera como válida.

## Resultados

Los resultados presentan una gran variación en función de la calidad de la imagen de la huella. 
