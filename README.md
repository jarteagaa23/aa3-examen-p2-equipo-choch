# Examen del Parcial II · Aprendizaje Automático III

IN1042 · Otoño 2026 · Grupo A7.

## Estado actual

Preparación documental y estructura de carpetas. Todavía no hay código, cuadernos, datos descargados, modelos entrenados ni resultados. Los entregables pendientes no se representan mediante archivos vacíos.

Número de equipo: pendiente de confirmar. El nombre definitivo del repositorio público debe ser `aa3-examen-p2-equipo-N`.

**Fecha límite del enunciado:** viernes 6 de noviembre de 2026, 23:59. Se entrega la liga del repositorio público en Moodle y se califica el último commit anterior al límite.

## Integrantes y contribuciones

Integrantes: pendientes de confirmar.

| Actividad | Responsable | Estado |
| --- | --- | --- |
| Estructura inicial y análisis de requisitos | Cuenta local jarteagaa23, con apoyo de Codex | Preparado |
| Desarrollo y revisión de CardioRitmo | Por asignar | Pendiente |
| Desarrollo y revisión de Compra Fácil Bajío | Por asignar | Pendiente |
| Folletos y maquetas | Por asignar | Pendiente |
| Integración y revisión final | Por asignar | Pendiente |

Cada integrante debe realizar sus propios commits. Esta tabla se actualizará con contribuciones reales verificables en el historial; no representa trabajo técnico ya terminado.

## Casos y criterios de aceptación

| Caso | Clase positiva | Requisitos en prueba, umbral 0.5 | Modelo elegido |
| --- | --- | --- | --- |
| CardioRitmo | Latido anormal | Sensibilidad ≥ 95 %, especificidad ≥ 95 % y modelo de máximo 20,000 parámetros | Pendiente; se elegirá mediante validación |
| Compra Fácil Bajío | Reseña negativa, de 1 o 2 estrellas | Exhaustividad ≥ 90 % y precisión ≥ 85 %; modelo entrenado por el equipo | Pendiente; se elegirá mediante validación |

## Organización

- `ecg/`: futuro cuaderno `DEV_ecg.ipynb`, `resultados_ecg.csv` y `folleto_ecg.pdf`.
- `ecg/modelo/`: modelo elegido de CardioRitmo.
- `resenas/`: futuro cuaderno `DEV_resenas.ipynb`, `resultados_resenas.csv` y `folleto_resenas.pdf`.
- `resenas/modelo/`: modelo elegido de Compra Fácil Bajío.
- `pmv/`: espacio opcional para aplicaciones locales del punto extra; su creación no implica que ya estén implementadas.
- `docs/`: análisis, plan de trabajo y lista de verificación.

Los archivos `.gitkeep` permiten conservar carpetas vacías en Git. Los cuadernos, CSV, PDF y modelos se agregarán cuando se desarrollen y verifiquen.

## Reglas de trabajo

1. Usar exactamente las fuentes, cargas y particiones de prueba indicadas en el examen.
2. Tomar decisiones de arquitectura, preparación y selección únicamente con entrenamiento y validación.
3. Reservar la prueba para una única evaluación final de la línea base y los modelos ya definidos; no reajustar después de ver sus resultados.
4. Evaluar a umbral fijo de 0.5. Reportar con honestidad cualquier incumplimiento.
5. Guardar los cuadernos ejecutados de arriba abajo y con salidas.
6. Mantener commits descriptivos en español y contribuciones propias de cada integrante.
7. Guardar cada modelo elegido en su carpeta `modelo/`. Si supera 100 MB, proporcionar en este README un enlace público de Hugging Face o Drive.

## Documentación

- [Análisis del examen](docs/analisis-examen.md).
- [Plan de trabajo y verificación](docs/plan-y-verificacion.md).

## Modelos y ejecución

Modelos elegidos y enlaces externos: pendientes.

Las instrucciones de instalación, ejecución, carga de modelos y PMV se documentarán cuando exista una implementación comprobada.
