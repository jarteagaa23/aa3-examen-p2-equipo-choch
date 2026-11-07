# CardioRitmo: tamizaje de latidos anormales

`DEV_ecg.ipynb` está ejecutado completo. Modelo elegido: **Conv1D** (5,857 parámetros, el límite es
20,000). En la prueba marca 99 de cada 100 latidos anormales (sensibilidad 99.3 %) y deja pasar
99 de cada 100 normales sin marcarlos (especificidad 99.1 %). **Cumple** las especificaciones.

## Contenido
- `DEV_ecg.ipynb`: exploración, preparación, línea base, Conv1D, GRU y su conjunto, elección y errores.
- `resultados_ecg.csv`: comparación de los modelos en la prueba.
- `modelo/modelo_ecg.keras`: modelo elegido (incluye su normalización).
- `folleto_ecg.pdf`: resumen ejecutivo para el director.

## Ejecutar
Python 3.11–3.13 con `tensorflow scikit-learn pandas matplotlib`. Abrir el cuaderno y correr todo.

## Limitación principal
Todos los latidos son de un solo paciente, así que solo está validado para ese paciente.
