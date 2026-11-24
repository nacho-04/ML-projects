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

## 📊 Resultados

AUC-ROC promedio en validación cruzada (K=5) con la mejor configuración de cada algoritmo:

| Modelo | AUC-ROC |
|---|---|
| **SVM (kernel RBF, C=100)** | **0.881** |
| KNN (k=17, distancia coseno) | 0.852 |
| Naïve Bayes | 0.729 |
| Árbol de decisión | 0.690 |
| LDA | 0.626 |

El mejor modelo (SVM) obtuvo un **AUC-ROC de 0.883 en el conjunto de control**, en línea con lo estimado en desarrollo. Los modelos que admiten fronteras no lineales y basadas en distancias (SVM, KNN) rinden mejor en este espacio de alta dimensión (200 genes, 400 muestras de desarrollo).

## 🧰 Tecnologías

Python · scikit-learn · pandas · NumPy · Matplotlib

## 📝 Notas

- El detalle de la metodología, los hiperparámetros y la discusión está en el [informe final](./Informe%20Final.pdf).
- Los datos provienen de la cátedra y pueden no ser redistribuibles; si es el caso, no están incluidos en el repositorio.

## 👤 Autores
- Mario Livia Auqui
- Facundo Sanchez
- Mauricio Enrich
- Tomas Mele
- Ignacio Lucas Rodriguez
