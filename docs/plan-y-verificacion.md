# Plan de trabajo y verificación

## Etapa actual: código de reseñas preparado, sin entrenamiento

- [x] Leer y revisar visualmente las cuatro páginas del examen.
- [x] Documentar requisitos, entregables, criterios de aceptación y rúbrica.
- [x] Crear las carpetas locales de trabajo y de modelos.
- [x] Iniciar historial con mensajes de commit en español.
- [x] Confirmar nombre del equipo: equipo-choch, por decisión del usuario.
- [x] Confirmar integrantes y matrículas en el README.
- [ ] Confirmar aceptación del nombre por el docente.
- [ ] Asignar responsables y revisores reales en el README.
- [x] Crear el repositorio público con el nombre elegido: `aa3-examen-p2-equipo-choch`.
- [x] Publicar y verificar la estructura y el historial remoto.

Por indicación del usuario se preparó `resenas/DEV_resenas.ipynb`, sin ejecutar sus celdas ni entrenar modelos. El código de CardioRitmo comentado por el equipo todavía no aparece en `main` al preparar esta actualización. Las casillas de cierre siguen pendientes hasta comprobar los resultados reales.

- [x] Preparar el cuaderno de reseñas con la carga y prueba prescritas.
- [x] Preparar línea base, Embedding + Conv1D y Embedding + BiLSTM.
- [x] Separar selección con validación y evaluación final de prueba.
- [x] Documentar dependencias e instrucciones de ejecución.
- [ ] Ejecutar entrenamiento cuando se autorice y revisar resultados.

## Orden de trabajo propuesto

1. Acordar responsables, preparación de datos, modelos candidatos y criterio de selección con validación.
2. Construir cada DEV con las cargas exactas, reservando prueba desde el inicio.
3. Explorar y graficar entrenamiento; preparar transformaciones sin fuga.
4. Entrenar línea base y al menos dos modelos por problema. Registrar configuración, parámetros y resultados de validación.
5. Elegir con validación y congelar preparación, candidatos y modelos; verificar límite de ECG y umbral 0.5.
6. Evaluar una vez en prueba los candidatos definidos, exportar resultados y analizar errores reales.
7. Guardar y comprobar la carga de los modelos elegidos y su preparación.
8. Elaborar maquetas y folletos con los resultados reales.
9. Considerar el PMV funcional opcional después de completar los entregables obligatorios.
10. Revisar archivos, salidas, consistencia e historial y entregar la liga en Moodle antes del límite.

## Lista de cierre: CardioRitmo

- [ ] Carga exacta, etiqueta 1 = anormal y prueba de 20 % estratificada con semilla 42.
- [ ] Entrenamiento y validación tomados solamente del resto.
- [ ] Tamaño, balance, ejemplos y al menos dos gráficas.
- [ ] Línea base trivial y al menos dos modelos admitidos, entrenados por el equipo.
- [ ] Modelo elegido con validación y máximo 20,000 parámetros totales.
- [ ] Prueba usada solo en la etapa final, con umbral 0.5.
- [ ] Sensibilidad, especificidad y AUC informadas; cumplimiento declarado con honestidad.
- [ ] `resultados_ecg.csv` con esquema requerido y solo un `elegido=True`.
- [ ] Justificación y tres errores del modelo elegido analizados.
- [ ] Modelo guardado en `ecg/modelo/` y carga comprobada.
- [ ] `DEV_ecg.ipynb` ejecutado de arriba abajo, guardado con salidas.
- [ ] `folleto_ecg.pdf` de máximo dos cuartillas, con maqueta, métricas, limitaciones respaldadas, aviso ético y mejora.
- [ ] Alcance limitado por datos de un único paciente explicado y respaldado en DEV.

## Lista de cierre: Compra Fácil Bajío

- [ ] Fuente y particiones oficiales exactas; estrellas = label + 1.
- [ ] Negativa = 1 o 2 estrellas, clase positiva = 1.
- [ ] Decisión sobre tres estrellas en entrenamiento justificada en una línea.
- [ ] Prueba oficial sin tres estrellas reservada para el final.
- [ ] Vocabulario, vectorizador y transformaciones aprendidos solo con entrenamiento.
- [ ] Tamaño, balance, ejemplos y al menos dos gráficas.
- [ ] Línea base trivial y al menos dos modelos admitidos entrenados por el equipo.
- [ ] Modelo elegido con validación; no depende de un LLM consultado por API.
- [ ] Prueba evaluada en la etapa final con umbral 0.5.
- [ ] Exhaustividad, precisión y exactitud informadas; cumplimiento declarado con honestidad.
- [ ] `resultados_resenas.csv` con esquema requerido y solo un `elegido=True`.
- [ ] Justificación y tres errores del modelo elegido analizados.
- [ ] Modelo y preparación necesarios para inferencia guardados; carga comprobada.
- [ ] `DEV_resenas.ipynb` ejecutado de arriba abajo, guardado con salidas.
- [ ] `folleto_resenas.pdf` de máximo dos cuartillas con todos los componentes pedidos.
- [ ] Limitaciones de cobertura entre Amazon España y tienda mexicana documentadas sin atribuirles efectos no medidos.

## Revisión de entrega

- [ ] Repositorio público `aa3-examen-p2-equipo-N`.
- [ ] README con integrantes, contribuciones reales y modelos elegidos.
- [ ] Historial con commits propios de cada integrante y mensajes en español.
- [ ] Cuadernos, CSV y folletos coinciden en modelos, métricas y cumplimiento.
- [ ] Archivos de modelos disponibles; enlaces públicos en README cuando superen 100 MB.
- [ ] Ningún entregable obligatorio es un marcador vacío.
- [ ] Si se entrega extra: app en `pmv/`, carga del modelo, clasificación, instrucciones y captura o video.
- [ ] Último commit entregable anterior al viernes 6 de noviembre de 2026 a las 23:59.
- [ ] Liga del repositorio enviada a Moodle por el equipo.
