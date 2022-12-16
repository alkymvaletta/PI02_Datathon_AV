<h1 align=center> **PROYECTO INDIVIDUAL Nº2**</h1>
<h1 align=center> **DATATHON** </h1>

<p align=center><img src=https://d31uz8lwfmyn8g.cloudfront.net/Assets/logo-henry-white-lg.png><p>

## **Introducción**

Estre proyecto consiste en la elaboración de modelo de Machine Leraning para un hospital, con el objetivo de determinar si los pacientes de este tendrán una estancia hospitalaria prolongada (más de 8 días); lo anterior tomando como base un dataset donde se encuentran alojados los datos históricos de los pacientes y la estancia de estos en el hospital.

Para determinar si la estancia de los pacientes en el hospital será prolongada o no, se empleará una [Red Neuronal](https://aws.amazon.com/es/what-is/neural-network/ "Red Neuronal") hecha con [TensorFlow](https://www.tensorflow.org/about "TensorFlow") y [Keras](https://keras.io/ "Keras").

## Exploración de los datos

Se realiza una exploración inicial de los datos contenido del dataset donde se encuentra el histórico de los datos, donde exploramos columna por columna que tipos de datos estan aquí contenidos y si la información que esta aporta es es relevante o no para determinar si el paciente puede tener una estancia prolongada en el hospital.

Se ajustan los datos contenidos en los dataset, en primer lugar se crea una columna nueva donde se establece si se ha tenido una estancia hospitalaria prolongada, posteriormente, se eliminan las columnas que no aportan información relevante, teniendo en cuenta la exploración de los datos que se realizó previamente.

Se establece el criterio de crear un OneHotEncoder a los datos considerados relevantes para establecer el criterio de predición, momento despues se considera tambíen el de realizar la categorización por medio de LabelEncoder.

## Diseño de Redes Neuronales

Se crea inicialmente una red neuronal con la ayuda de las librerías TensorFlow y Keras, en la cual se somete a diversas prueba a fin de determinar la cantidad de capas capas necesarias, las épocas necesarias para su entrenamiento, el optimizador y el peso del ajuste para que sí se presentara un aprendizaje.

Se presentaron las siguientes particularidades:
 - **Red Neuronal 1:** Fue la primera red creada, se realizaron diferentes pruebas ajustando los parametros hasta notar que si se realizo un aprendijase en esta. Se destaca que se evidenció que despues de 2000 datos para el entrenamiento no se nbotaba mejoría, además era suficiente con 500 épocas. Con esta se realizó el primer modelo, que se encuentra en la carpeta Modelos con el nombre RN_1.h5 .
 
 - **Red Neuronal 2:** Para esta red se consideró realizar una "mejora" aportando los datos con LabelEncoder, lo cual, una vez realizadas las pruebas iniciales, demostro que se requerían más datos para obtener un mejor aprendizaje, por lo que se elevaron a 10.000 debido a que esta fue más propensa a realizar ruido. Finalmente el modelo no fue el mejor, ofrecía un recall muy alto con los datos 1.
 
- **Red Neuronal 3:** Tomando como base los datos obtenidos en la red 2, se comprendio que era necesario seguir mejorando la red 1 y que se mejoraba los resultados teniendo más columnas, por lo que ahora tratamos de mejorar cambiando la función de pérdida, por lo cual despues de ensayar, se estableció las más optima era *mean_squared_logarithmic_error*, lo que llevo a una mejora en el modelo.

## Que encontrarás en este repositorio
1. **Dataset**: contiene los archivos de *"train"* y *"test"* con los que se trabajó.
2. **DF_Dummis_RN**: contiene los archivos con los ajustes necesarios para el entrenamiento y test en la red neuronal 1 y 3, estos archivos se realizaron con *One Hot Encoder*.
3. **DF_LE_RN:** contiene los archivos con los ajustes necesarios para el entrenamiento y test en la red neuronal 2, estos archivos se realizaron con *Label Encoder*.
4. **Modelos:** contiene archivos donde se exportaron los modelos que se entrenaron con la red neuronal. Para ser cargados se deben seguir las instrucciones en este [link](https://www.tensorflow.org/guide/keras/save_and_serialize#registering_the_custom_object "link").
5. **Predicciones:**  contiene el resultante de correr los datos de *test* en el modelo resultante de la red neuronal.
6. **Redes_Neuronales:** contiene los archivo "*ipynb" donde en los que se creó las diferentes redes neuronales.
7. **EDA_ETL.ipynb:** Es el archivo donde se realizo todo el proceso exploratorio y de ajuste de los datos para poder ser tratados.


## Métricas.
En la medición de la efectividad del modelo juegan un papel importante el [accuracy](http://https://developers.google.com/machine-learning/crash-course/classification/accuracy "accuracy"), el [recall](https://developers.google.com/machine-learning/crash-course/classification/precision-and-recall "recall") y adicionalmente la curva ROC y AUC. Teniendo como principal objetivo del modelo la mejora de este último, a su vez que el balanceo del accuracy con el recall

