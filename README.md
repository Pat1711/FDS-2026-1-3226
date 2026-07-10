# Proyecto de Predicción de Visualizaciones en Tendencias de YouTube México

## ▪ Objetivo del proyecto
El objetivo principal de este proyecto es desarrollar, evaluar y validar un modelo de **Regresión Lineal Múltiple** capaz de predecir el éxito de un video (medido a través de su volumen de visualizaciones) cuando se posiciona dentro de la pestaña de Tendencias de YouTube en México. El modelo busca entender la influencia de las interacciones tempranas de los usuarios y las características estructurales del contenido en su rendimiento final.

---

## ▪ Nombre de los alumnos participantes
* [PATRICIA GIOVANNA GUIMARAY MEJIA  - U202410943]
* [SEBASTIÁN YENCO GOMEZ ANGELES - U20241A594]
* [JAIRO NAIM RAMSELL HUASAJA TORRES - U202312816]
* [MELISSA DANERY QUISPE SUCASACA - U202420282]

---

## ▪ Breve descripción del conjunto de datos
El conjunto de datos comprende registros históricos de los videos que han alcanzado la sección de Tendencias en la plataforma de YouTube para el mercado mexicano. Debido a la naturaleza altamente sesgada y exponencial de las métricas de redes sociales, el dataset fue sometido a un proceso de ingeniería de características y transformación logarítmica (`log1p`) para estabilizar la varianza. 

Las variables clave seleccionadas para el modelado definitivo son:
* **`log_views` (Variable Objetivo):** Logaritmo natural del total de reproducciones del video.
* **`log_likes` (Variable Predictora):** Logaritmo natural del conteo de "Me gusta", utilizado como el indicador principal de interacción (*engagement*).
* **`category_popularity_rank` (Variable Predictora):** Rango numérico que mide la popularidad histórica de la categoría a la que pertenece el video dentro de las tendencias.
* **`num_tags` (Variable Predictora):** Cantidad total de etiquetas (palabras clave) configuradas por el creador en el video.
* **`title_length` (Variable Predictora):** Longitud en caracteres del título del video.

---

## ▪ Conclusiones

### 1. Diagnóstico Visual y Cumplimiento de Supuestos (Análisis de Gráficos)
El análisis visual de los gráficos de diagnóstico confirma que el modelo cumple satisfactoriamente con los supuestos estadísticos clave de la Regresión Lineal:
* **Ajuste Lineal Continuo:** Al observar la relación entre los *Valores Reales vs. Predichos*, se aprecia una única nube de puntos densa y homogénea que abraza de manera estrecha y ascendente la línea diagonal de predicción perfecta ($Y=X$). Esto demuestra que la transformación logarítmica aplicada a las variables de interacción fue una decisión metodológica correcta, logrando estabilizar una distribución que originalmente era exponencial para permitir que el algoritmo lineal opere con alta efectividad en todo el espectro de datos.
* **Homocedasticidad y Estabilidad del Error:** El gráfico de residuos evidencia un comportamiento sumamente saludable. Los errores de predicción se distribuyen de forma simétrica y aleatoria por encima y por debajo de la línea horizontal de error cero, sin exhibir patrones geométricos marcados o distorsiones estructurales (como formas de embudo o dispersiones anómalas). Esto valida el supuesto de homocedasticidad, garantizando que el modelo mantiene un nivel de varianza y predictibilidad constante a lo largo de los diferentes volúmenes de vistas estimados.

### 2. Capacidad Explicativa y Precisión General ($R^2$ y MAE)
El modelo entrenado logra explicar el **62.23% de la varianza total** del éxito de un video, lo cual representa un coeficiente de determinación ($R^2$) sumamente robusto para el análisis de plataformas digitales y comportamiento de audiencias. Respaldado por un **MAE Real de 169,470 vistas**, podemos concluir que el algoritmo funciona como una herramienta de negocio confiable y precisa para estimar el rendimiento de los videos que experimentan un ciclo de vida orgánico estándar dentro de la sección de Tendencias en YouTube México.

### 3. El Fenómeno de la Viralidad Extrema (El Límite del Modelo Lineal)
A pesar del excelente ajuste geométrico de los datos, los resultados también permiten identificar con claridad los límites de la linealidad frente a la naturaleza misma de internet. 
Al observar el extremo superior derecho del primer gráfico, se aprecia que los puntos que representan las visualizaciones más altas tienden a dispersarse y ubicarse ligeramente por encima de la línea roja de predicción. Asimismo, el RMSE Real (~967,000 vistas) se posiciona notablemente por encima del MAE. 

Esta discrepancia matemática indica que el modelo **tiende a subestimar el alcance real de los videos "Mega-Virales"**. Al elevar los errores al cuadrado, el RMSE captura y penaliza con severidad estos desvíos extraordinarios, concluyendo que el crecimiento explosivo e impredecible de un gran fenómeno de masas responde a factores intangibles (como la tasa de retención de la audiencia, el impacto cultural del momento o el empuje del algoritmo de recomendación externa) que escapan a la capacidad de una ecuación lineal tradicional.

---

## ▪ Licencia de uso
Este proyecto se distribuye bajo la licencia **MIT**. Eres libre de usar, modificar y distribuir este código para fines académicos o comerciales, siempre y cuando se otorgue el crédito correspondiente a los autores originales. 

Consulta el archivo `LICENSE` para obtener más detalles.