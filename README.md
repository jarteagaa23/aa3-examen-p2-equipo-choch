# aa3-examen-p2-equipo-choch

Examen del Parcial II · IN1042 Aprendizaje Automático III · Otoño 2026

## Integrantes
- Josué Abraham Arteaga Manrique (18910-1)
- Edgar Mauricio Trejo Delgado (192583-4)

## Quién hizo qué
| Integrante | Trabajo |
|---|---|
| Josué Arteaga | Problema 2 (reseñas): `DEV_resenas.ipynb` (carga, exploración, vectorización, línea base, modelos Embedding + Conv1D y Embedding + BiLSTM, evaluación de prueba), `resenas/README.md` y `folleto_resenas.pdf`. |
| Mauricio Trejo | Problema 1 (ECG) completo: `DEV_ecg.ipynb`, modelos, `resultados_ecg.csv`, modelo guardado y `folleto_ecg.pdf`. Problema 2: ejecución del cuaderno. |

Usamos herramientas de IA como apoyo, como lo permite el examen.

## Modelos elegidos
| Problema | Modelo elegido | Resultado en la prueba | ¿Cumple? |
|---|---|---|---|
| 1 · CardioRitmo (latidos) | **Conv1D** (5,857 parámetros) | Sensibilidad 99.3 %, especificidad 99.1 % | Sí |
| 2 · Compra Fácil Bajío (reseñas) | **Embedding + Conv1D** | Exhaustividad 93.2 %, precisión 91.1 % | Sí |

## Estructura
```
README.md
ecg/       DEV_ecg.ipynb, resultados_ecg.csv, modelo/, folleto_ecg.pdf
resenas/   DEV_resenas.ipynb, resultados_resenas.csv, modelo/, folleto_resenas.pdf
```
