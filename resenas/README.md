# Compra Fácil Bajío: preparación del entrenamiento

`DEV_resenas.ipynb` está ejecutado completo. Modelo elegido: **Embedding + Conv1D**, que en la
prueba marca 93 de cada 100 reseñas negativas (exhaustividad 93.2 %) y acierta en 91 de cada 100
que marca (precisión 91.1 %). **Cumple** las especificaciones del cliente.

## Abrir el cuaderno

Desde la raíz del repositorio, con Python 3.11 o 3.12:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r resenas/requirements.txt
python -m ipykernel install --user --name aa3-examen-p2 --display-name "AA3 Examen P2"
jupyter lab resenas/DEV_resenas.ipynb
```

También se puede abrir en VS Code y seleccionar el intérprete de `.venv`. En Windows, activar con `.venv\Scripts\activate`.

Se necesita conexión para descargar las particiones oficiales cuando se ejecute la carga. Una GPU puede acelerar el entrenamiento, pero el código no la exige. Las dependencias se especifican como rangos; el cuaderno registra las versiones utilizadas al ejecutarse. La ejecución con TensorFlow aún no se ha comprobado.

## Desarrollo y selección

1. Leer las decisiones metodológicas del cuaderno y ejecutar en orden hasta la preparación.
2. La carga reproduce la indicada en el examen. `test` queda reservado; la exploración y el vocabulario usan entrenamiento. Se excluyen tres estrellas tanto de entrenamiento como de validación para comparar la misma tarea binaria que pide el cliente.
3. Revisar en entrenamiento el balance, los ejemplos y las gráficas. Las longitudes se limitan inicialmente a 180 tokens y el vocabulario a 20,000 términos; cualquier cambio debe decidirse sin consultar prueba.
4. Para entrenar, cambiar `ENTRENAR = False` a `True` en la configuración y ejecutar el cuaderno desde el inicio. El valor inicial detiene el cuaderno antes de `fit`.
5. Se comparan la clase mayoritaria, Embedding + Conv1D y Embedding + BiLSTM. Las dos redes aprenden sus propios embeddings. Se usa parada temprana con pérdida de validación y restauración de los mejores pesos.
6. El modelo vendido se elige entre las dos redes mediante validación: primero cumplimiento de ambos requisitos, después el menor de los cocientes exhaustividad/0.90 y precisión/0.85, F1 y menor número de parámetros para desempatar. El umbral siempre es 0.5.
7. El cuaderno guarda el modelo elegido con su vectorizador integrado, comprueba la recarga con textos de validación y registra selección, configuración, historiales y versiones en `modelo/`.

La línea base es referencia, no uno de los dos modelos del parcial. No se garantiza cumplimiento antes de medirlo. La validación se utiliza también para parada temprana y por ello no sustituye a prueba.

## Evaluación final reservada

`EVALUAR_PRUEBA = False` es independiente de `ENTRENAR`. Mantenerlo así mientras se toman decisiones. Tras congelar los candidatos y el modelo elegido, cambiarlo a `True` y ejecutar la celda final en la misma sesión, después del entrenamiento y guardado. Esa etapa evalúa una vez los tres candidatos al umbral 0.5 y produce:

- `resultados_resenas.csv`: DataFrame `resultados` con todas las columnas exigidas.
- `errores_resenas.csv`: hasta tres errores del modelo elegido y campos pendientes de análisis humano.
- `modelo/evaluacion_prueba.json`: constancia de inicio y terminación para impedir evaluaciones repetidas accidentales.

Si ya existe la constancia, la celda carga los resultados guardados y **no vuelve a predecir**. Si una evaluación quedó interrumpida, se detiene y pide revisar su estado; no borrar el registro para seguir ajustando contra prueba. Una ejecución simultánea queda bloqueada mediante creación exclusiva del registro.

La revisión final debe completar la explicación de tres errores reales en el cuaderno, actualizar el modelo elegido y sus métricas en el README general, elaborar el folleto y guardar el cuaderno con salidas. Si hay menos de tres errores, documentar el número real y revisar la exigencia con el docente; no inventar errores.

## Límites previstos

- Los datos son de Amazon España y el cliente es una tienda mexicana. La cobertura de lenguaje local deberá evaluarse con otros datos antes de prometer desempeño en ese contexto.
- Las estrellas son una aproximación al sentimiento y se excluye el caso neutral de tres estrellas.
- La normalización conserva negaciones y acentos, pero elimina puntuación; el truncado puede perder información. El DEV cuantifica el truncado en entrenamiento y validación.
- El análisis de errores deberá establecer cuáles de estas limitaciones aparecen realmente y darles respaldo cuantitativo para el folleto.

Referencias de implementación: [TextVectorization](https://keras.io/api/layers/preprocessing_layers/text/text_vectorization/) y [guardado y serialización de Keras](https://www.tensorflow.org/guide/keras/serialization_and_saving).
