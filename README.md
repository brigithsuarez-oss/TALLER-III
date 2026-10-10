# Maestría en Ciencia de Datos - Taller III
  ### UNIVERSIDAD YACHAY TECH 
### María Brigith Suárez Rodríguez 

# Título: Análisis de Redes y Sistemas de Recomendación


## Objetivos:


1.	Análisis de Redes:
a.	Entender y aplicar teoría de grafos para analizar los datos de interacciones entre usuarios y películas.
b.	Identificar nodos centrales, comunidades y otras métricas de red utilizando networkx.
c.	Visualizar la estructura del grafo e interpretar los resultados.
2.	Sistemas de Recomendación:
a.	Implementar sistemas de recomendación colaborativa utilizando la librería surprise.
b.	Evaluar diferentes algoritmos (SVD, KNN) y comparar métricas de rendimiento.
c.	Entender cómo ajustar hiperparámetros para mejorar la precisión de las recomendaciones.


### Parte 1: Análisis de Redes con networkx
Paso 1: Preparación del Conjunto de Datos

●	Carga el conjunto de datos de MovieLens y extrae las interacciones entre usuarios y películas. Crearás un grafo bipartito donde los usuarios están conectados con las películas que han valorado.
### Paso 2: Análisis del Grafo
 
1.	Centralidad de Grado: Identifica a los usuarios más activos y las películas más populares.
2.	Coeficiente de Agrupamiento: Analiza el agrupamiento de usuarios y películas.
3.	Detección de Comunidades: Aplica algoritmos de detección de comunidades (e.g., Girvan-Newman).
4.	Visualización: Visualiza una parte de la red utilizando matplotlib.

Grafo Bipartito Validado: La verificación de estructura arrojó True, lo que confirma que es un grafo bipartito válido (donde las conexiones existen únicamente entre usuarios y películas, nunca entre usuarios-usuarios ni películas-películas).
Nodos: El grafo contiene un total de 20,668 nodos, divididos de forma exacta en: 610 usuarios únicos (etiquetados como u_ID). 9,724 películas únicas (etiquetadas como m_ID).
Interacciones (Aristas): Se crearon exitosamente 100,836 aristas correspondientes a las valoraciones realizadas por los usuarios, incluyendo el peso de su respectiva calificación (atributo rating).


Este bloque de código abordará los cuatro puntos solicitados:

- Centralidad de Grado: Encontrará los usuarios que han calificado más películas y las películas más valoradas.
- Coeficiente de Agrupamiento Bipartito: Calculará el agrupamiento para conocer la interconectividad.
- Detección de Comunidades: Aplicará un algoritmo de detección de comunidades en grafos bipartitos.
- Visualización: Generará un gráfico representativo de una subred de usuarios y películas.



#### Tareas de Desafío:

●	Identifica los 5 usuarios que califican más películas.
●	Determina cuáles son las películas más centrales en la red.
●	Visualiza la red con un enfoque en las comunidades.

###### 1. Los 5 Usuarios Más Activos
Son aquellos con mayor centralidad de grado (quienes han calificado más películas):

- Usuario 414: Centralidad de 0.26111 (ha calificado 2,698 películas).
- Usuario 599: Centralidad de 0.23981 (ha calificado 2,478 películas).
- Usuario 474: Centralidad de 0.20401 (ha calificado 2,108 películas).
- Usuario 448: Centralidad de 0.18039 (ha calificado 1,864 películas).
- Usuario 274: Centralidad de 0.13026 (ha calificado 1,346 películas).

###### 2. Las Películas Más Centrales (Populares)

Corresponden a las películas con mayor cantidad de valoraciones por parte de la comunidad de usuarios:

- Forrest Gump (ID: 356): Centralidad de 0.03184 (329 calificaciones).
- The Shawshank Redemption / Sueños de Fuga (ID: 318): Centralidad de 0.03068 (317 calificaciones).
- Pulp Fiction (ID: 296): Centralidad de 0.02971 (307 calificaciones).
- The Silence of the Lambs / El Silencio de los Inocentes (ID: 593): Centralidad de 0.02700 (279 calificaciones).
- The Matrix (ID: 2571): Centralidad de 0.02690 (278 calificaciones).

###### 3. Visualización con Enfoque en Comunidades
La imagen generada por la última celda de tu cuaderno (d2a02d74) muestra una subred que conecta a estos 5 usuarios súper activos con sus películas más relevantes.

- Nodos circulares: Representan a los usuarios.
- Nodos cuadrados: Representan a las películas.
- Colores: Los nodos están coloreados dinámicamente según la comunidad a la que pertenecen, utilizando el algoritmo de modularidad de Clauset-Newman-Moore. Las conexiones (aristas) grises reflejan el flujo de las calificaciones entre ellos.
¡Hemos completado con éxito todo el flujo de análisis solicitado para el conjunto de datos de MovieLens!

###### Resumen del Proceso:
Preparación y Carga: Implementamos una descarga automática del dataset desde Colab, resolviendo el problema de acceso a las rutas locales.
Construcción del Grafo: Creamos un grafo bipartito con networkx compuesto por 10,334 nodos (610 usuarios y 9,724 películas) y 100,836 interacciones (valoraciones), asegurando identificadores únicos y consistentes.
Identificación de Usuarios Activos: Identificamos que el Usuario 414 es el más activo de la red con 2,698 valoraciones.
Identificación de Películas Centrales: Encontramos que Forrest Gump (ID: 356) es la película más central de la red con 329 calificaciones.
Comunidades y Visualización: Dividimos la red en comunidades basadas en la optimización de modularidad y generamos una visualización interactiva de una subred donde los nodos (usuarios y películas) se colorean según su comunidad correspondiente.

### Parte 2: Sistema de Recomendación con surprise
#### Paso 1: Preparación del Conjunto de Datos

●	Carga los datos de MovieLens en el formato requerido por surprise.

Dado que la biblioteca scikit-surprise no viene preinstalada en el entorno estándar de Colab, primero añadiremos una celda para instalarla. Luego, crearemos las celdas necesarias para:

- Cargar los datos de MovieLens al formato de surprise.
- Entrenar y evaluar los modelos SVD (Factorización de Matrices) y KNN (Filtrado Colaborativo Basado en Vecindario).
- Ajustar hiperparámetros usando GridSearchCV para encontrar la configuración óptima.

### Paso 2: Entrenamiento del Modelo

1.	Filtrado Colaborativo usando Factorización de Matrices (SVD):
2.	KNN Usuario-Usuario o Ítem-Ítem: Paso 3: Ajuste de Hiperparámetros
#### Paso 3:Ajusta los hiperparámetros 
Ajusta los hiperparámetros (e.g., n_factors, k) para optimizar el rendimiento utilizando grid search.

#### Tareas de Desafío:

●	Compara el rendimiento de los modelos SVD y KNN en términos de RMSE.
●	Optimiza los hiperparámetros para obtener el RMSE más bajo posible.
●	Genera recomendaciones de las 5 mejores películas para un usuario específico.


●	Optimiza los hiperparámetros para obtener el RMSE más bajo posible.
●	Genera recomendaciones de las 5 mejores películas para un usuario específico.
