# Análisis del examen

Fuente: examen IN1042, Parcial II, caso aplicado, cuatro páginas. Este documento resume sus requisitos y distingue las propuestas de trabajo, todavía sujetas a validación. No contiene resultados experimentales.

## Alcance y entrega

- El examen vale 40 % del Segundo Parcial y se realiza con el equipo del proyecto.
- Publicación: jueves 5 de noviembre de 2026, 14:00. Límite: viernes 6 de noviembre de 2026, 23:59.
- Un repositorio público por equipo, `aa3-examen-p2-equipo-N`, y su liga en Moodle.
- Se deben resolver ambos casos y producir, para cada uno, un cuaderno DEV, un CSV de comparación, el modelo elegido y un folleto PDF de máximo dos cuartillas.
- Se permiten herramientas e IA, pero el equipo debe entender y poder explicar todo lo entregado.
- Cada integrante debe subir su trabajo con sus propios commits; el README y el historial deben coincidir.
- Un cuaderno sin salidas no puede calificarse. Cuenta el último commit anterior a la fecha límite.

## CardioRitmo: tamizaje de latidos

### Problema y aceptación

Marcar latidos anormales de registros Holter para que un cardiólogo los revise.

Con umbral fijo de 0.5, el modelo vendido debe alcanzar en prueba sensibilidad ≥ 0.95 y especificidad ≥ 0.95, y tener como máximo 20,000 parámetros. También se debe explicar a qué pacientes se puede extender lo observado.

### Datos y particiones obligatorias

- ECG5000: el enunciado describe 4,998 latidos de 140 puntos, ya normalizados.
- Fuente exacta: https://storage.googleapis.com/download.tensorflow.org/data/ecg.csv
- Lectura sin encabezado. Características: todas las columnas excepto la última, en float32.
- Etiqueta: invertir la última columna; en el trabajo, 1 significa ANORMAL y 0 normal.
- Separar exactamente 20 % de prueba con estratificación por etiqueta y semilla 42, usando la división indicada en el PDF.
- Formar entrenamiento y validación únicamente con el 80 % restante.
- Mantener intacto el bloque de carga y división del enunciado al implementar; aquí no se reproduce ni ejecuta código.

### Modelos y decisiones pendientes

El examen admite MLP, Conv1D, TCN, RNN, LSTM y GRU, incluidas variantes bidireccionales y apiladas. Se requieren una línea base trivial y al menos dos modelos del parcial entrenados por el equipo.

Propuesta inicial, no decisión final: comparar una MLP pequeña y una Conv1D pequeña con una línea base de clase mayoritaria. Las arquitecturas y sus tamaños se definirán más adelante con validación.

No cambiar la normalización disponible sin una justificación. Cualquier transformación que aprenda estadísticas se ajustará solo con entrenamiento. El límite del dispositivo se revisará con el total de parámetros; el CSV debe informar específicamente los parámetros entrenables que pide el enunciado.

### Limitaciones que deberán evaluarse

Los latidos proceden de un Holter de 20 horas de un único paciente con insuficiencia cardiaca, de la base BIDMC de PhysioNet. La prueba aleatoria indicada no demuestra generalización a pacientes nuevos. No se debe afirmar validación clínica ni sustitución del cardiólogo. Las limitaciones del folleto deberán vincularse con cifras o errores observados en el DEV.

## Compra Fácil Bajío: reseñas negativas

### Problema y aceptación

Priorizar reseñas negativas para atención a clientes. Negativa significa 1 o 2 estrellas y constituye la clase positiva.

En prueba, a umbral 0.5: exhaustividad ≥ 0.90 y precisión ≥ 0.85. El equipo debe entrenar el modelo; consultar un LLM mediante API no satisface este requisito.

### Datos y particiones obligatorias

- Amazon Multilingual Reviews, español, Keung et al. (2020), reseñas escritas en Amazon España.
- Fuente exacta: https://huggingface.co/datasets/SetFit/amazon_reviews_multi_es/resolve/main/{}.jsonl
- Particiones proporcionadas: train con 200,000 reseñas; validation con 5,000; test con 5,000.
- Estrellas = label + 1. Usar el texto del campo `text`.
- Prueba del cliente: partición test excluyendo tres estrellas, 4,000 reseñas, mitad negativas según el enunciado.
- Etiqueta de prueba: 1 cuando estrellas ≤ 2; 0 en caso contrario.
- No sustituir las particiones oficiales ni crear otra prueba.
- Mantener intacta la carga y definición de prueba del PDF cuando se implemente.

### Modelos y decisiones pendientes

Opciones admitidas: bigramas o TF-IDF con red densa; Embedding con LSTM, Bi-LSTM o Conv1D; embeddings preentrenados con un clasificador entrenado encima; BETO ajustado.

Propuesta inicial: línea base de clase mayoritaria, TF-IDF con red densa y Embedding con Conv1D. No se han seleccionado definitivamente ni entrenado modelos.

El equipo debe decidir si excluye las reseñas de tres estrellas del entrenamiento o las asigna a una clase, y justificarlo en una línea. Una propuesta razonable a evaluar es excluirlas para alinear la tarea con la prueba. Si se filtra validación para comparar con la misma definición binaria, se documentará ese tratamiento. Vocabulario, vectorizador y cualquier transformación aprendida se ajustarán solo con entrenamiento.

### Limitaciones que deberán evaluarse

El origen español de las reseñas plantea una posible diferencia con el lenguaje y los productos de una tienda mexicana. Es una limitación de cobertura por investigar, no un deterioro de desempeño ya medido. Se deberán examinar errores concretos como negaciones, ironía, textos ambiguos o quejas de logística si aparecen realmente. No se inventarán ejemplos fallidos.

## Requisitos comunes del cuaderno DEV

1. Exploración: tamaño, balance de clases, ejemplos y al menos dos gráficas por problema. Para no usar prueba anticipadamente, explorar entrenamiento y documentar validación cuando corresponda.
2. Preparación: partición prescrita, transformaciones justificadas y ausencia de fuga de información.
3. Entrenamiento: línea base trivial y al menos dos modelos del parcial entrenados por el equipo.
4. Elección: decidir con validación arquitectura, hiperparámetros, preparación y modelo vendido antes de evaluar prueba.
5. Evaluación final: comparar línea base y modelos ya fijados en una sola etapa final sobre prueba, al umbral 0.5. No volver a ajustar tras conocerla.
6. Crear un DataFrame llamado `resultados` y exportarlo como el CSV correspondiente.
7. Justificar el modelo elegido y analizar tres errores reales que cometa.
8. Guardar el modelo elegido y ejecutar el cuaderno completo, de arriba abajo, conservando sus salidas.

La regla de prueba única y la comparación de varios modelos se interpretan conjuntamente: se congela primero el conjunto de candidatos y se evalúan una vez al final. Para reproducir posteriormente el cuaderno con salidas, no se deben usar esas ejecuciones para tomar nuevas decisiones ni iniciar ciclos de ajuste sobre prueba.

### Esquema de resultados

| Campo | ECG | Reseñas |
| --- | --- | --- |
| modelo | Nombre | Nombre |
| tipo | Categoría del enunciado | Categoría del enunciado |
| parametros | Número de parámetros entrenables | Número de parámetros entrenables |
| Métricas | sensibilidad, especificidad, auc | exhaustividad, precision, exactitud |
| cumple | Todas las condiciones, incluido tamaño | Todas las condiciones del cliente |
| elegido | True solo para el modelo vendido | True solo para el modelo vendido |

Valores de `tipo` enumerados por el PDF: `linea base`, `recurrente`, `convolucional`, `conjunto`, `embeddings`, `transformer`. El examen admite MLP pero no enumera una categoría `denso`; si se elige una MLP, habrá que aclarar esa clasificación y documentar el criterio antes de cerrar el CSV.

No sustituir sensibilidad por exactitud ni confundir precisión con exhaustividad. Calcular AUC con puntuaciones continuas. Comparar los valores completos con los requisitos antes de redondear para presentación.

### Modelo guardado

Guardar el modelo elegido dentro de `modelo/` del problema. Si supera 100 MB, alojarlo en Hugging Face o Drive con enlace público en el README. Para texto, conservar además los elementos de preparación necesarios para reproducir las predicciones, como vocabulario o vectorizador. Verificar que el artefacto guardado se puede cargar y usar.

## Folleto ejecutivo por empresa

Máximo dos cuartillas en PDF, dirigido al director, con:

- Problema y propuesta de valor.
- Imagen de la interfaz del PMV; basta una maqueta.
- Desempeño en palabras del cliente y declaración explícita de cumplimiento o incumplimiento.
- Limitaciones, cada una respaldada por un número o error del DEV.
- Aviso ético y propuesta de mejora.

Los números del folleto deben coincidir con el CSV y el cuaderno. Se redactará después de la evaluación para no inventar desempeño.

## Calificación

Cada problema vale 100 puntos. La nota del examen es el promedio de ambos y se comparte en el equipo.

| Bloque | Criterio | Puntos por problema |
| --- | --- | --- |
| DEV | Datos y exploración con gráficas | 10 |
| DEV | Preparación y división sin fuga | 10 |
| DEV | Línea base y al menos dos modelos comparados | 20 |
| DEV | Cumplimiento en prueba | 10 |
| DEV | Elección, tres errores y modelo guardado | 10 |
| Folleto | Propuesta de valor y maqueta | 10 |
| Folleto | Desempeño en lenguaje del cliente | 10 |
| Folleto | Limitaciones respaldadas por el DEV | 10 |
| Folleto | Aviso ético y mejora | 5 |
| Folleto | Claridad y máximo dos cuartillas | 5 |

Si no se cumplen las especificaciones, reconocerlo en el folleto y explicar qué falta permite obtener 5 de los 10 puntos de cumplimiento.

El extra es opcional: una app web local por caso que cargue el modelo guardado y clasifique, en `pmv/`, con instrucciones en README y captura o video corto. Cada app suma 0.5 puntos a la calificación final del Segundo Parcial, hasta 1 punto por ambas, sin superar 10. La maqueta obligatoria del folleto no equivale por sí sola a este extra.
