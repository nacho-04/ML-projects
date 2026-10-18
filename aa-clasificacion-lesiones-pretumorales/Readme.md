# Clasificación de lesiones pre-tumorales

**Materia:** Aprendizaje Automático · Departamento de Computación, FCEN, UBA · 2.º cuatrimestre 2026
**Tipo de trabajo:** Trabajo práctico grupal

## 🎯 Objetivo

Predecir el pronóstico (buen pronóstico = 1, mal pronóstico = 0) de pacientes con lesiones pre-tumorales a partir de mediciones de ARN de 200 genes obtenidas por secuenciación de nueva generación (NGS). El dataset tiene 500 muestras, así que el foco está en estimar con realismo la performance y evitar sobreajuste.

## 🔬 Qué se hizo

1. **Separación de datos:** esquema propio de desarrollo/evaluación (sin `train_test_split`) y justificación de las decisiones.
2. **Árboles de decisión:** validación cruzada K-fold (K=5) con Accuracy, AUPRC y AUCROC; exploración de altura máxima y criterio de corte con `ParameterGrid`.
3. **Comparación de algoritmos** con `RandomizedSearchCV` (métrica: AUCROC, 5 folds):
   - Árboles de decisión, KNN y SVM con búsqueda de hiperparámetros.
   - LDA y Naïve Bayes como referencia con hiperparámetros por defecto.
4. **Evaluación final:** estimación del AUCROC del mejor modelo sobre un conjunto de control y predicción de probabilidades.
5. **Conclusiones** y análisis de problemas encontrados.


## 🧰 Tecnologías

Python · scikit-learn · pandas · NumPy · Matplotlib

## 📝 Notas

- Los datos provienen de la cátedra y pueden no ser redistribuibles; si es el caso, no están incluidos en el repositorio.

## 👤 Autores
- Mario Livia Auqui
- Facundo Sanchez
- Mauricio Enrich
- Tomas Mele
- Ignacio Lucas Rodriguez
