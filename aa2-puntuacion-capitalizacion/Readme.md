# Predicción de puntuación y capitalización en texto normalizado

**Materia:** Aprendizaje Automático II · Departamento de Computación, FCEN, UBA · 2.º cuatrimestre 2026
**Tipo de trabajo:** Trabajo práctico grupal

## 🎯 Objetivo

Dado un texto en minúsculas y sin puntuación (como la salida de un sistema de reconocimiento de voz, ASR), predecir para cada palabra la **puntuación inicial** (`¿`), la **puntuación final** (`,` `.` `?`) y la **capitalización** (minúsculas, inicial, mixta como *McDonald's* o todo en mayúsculas como *UBA*).

```
Entrada: cuándo salimos para la uba ya se hace tarde por dónde andarán
Salida:  ¿Cuándo salimos para la UBA? Ya se hace tarde. ¿Por dónde andarán?
```

## 🔬 Qué se hizo

1. **Datos:** 100 mil oraciones de Europarl (formal) y 100 mil de OPUS-100 (conversacional). Se descartan las oraciones con otros signos y se arman instancias de 10 a 50 palabras que cortan oraciones, para evitar el sesgo posicional (mayúscula al inicio, punto al final).
2. **Separación desarrollo / control** por documento, estratificando por fuente.
3. **Modelos:**
   - Baseline dummy (predice siempre la clase mayoritaria).
   - Random Forest con atributos hechos a mano o con embeddings estáticos de `bert-base-multilingual-cased`, con ventana de palabras vecinas.
   - RNN unidireccionales y bidireccionales (RNN simple, LSTM, GRU), con pérdida básica y con ponderación por incertidumbre de Kendall.
4. **Evaluación:** F1 macro por palabra en las 3 tareas, con umbrales de decisión ajustados para las clases poco frecuentes.
5. **Evaluación final** del mejor modelo, una sola vez, sobre el conjunto de control.

## 📊 Resultados

F1 macro por palabra, promedio de las 3 tareas:

| Modelo | Desarrollo | Control |
|---|---|---|
| Baseline (dummy) | 0.323 | – |
| Random Forest (embeddings, ventana 1) | 0.591 | – |
| RNN unidireccional (GRU, 1 capa) | 0.648 | – |
| **RNN bidireccional (LSTM, 1 capa)** | **0.755** | **0.753** |

El contexto es lo que más aporta: pasar de uni- a bidireccional suma ~0.10, sobre todo en la puntuación final. Las clases más difíciles siguen siendo la capitalización mixta y los signos de pregunta.

## 🧰 Tecnologías

Python · PyTorch · Hugging Face Transformers y Datasets · scikit-learn · pandas · Matplotlib

## 📝 Notas

- El detalle de la arquitectura y los resultados está en el [póster](./Tp2_AA_poster.pdf).
- Los datos de entrenamiento se descargan de Hugging Face. El archivo de evaluación de la cátedra (`datos_test.csv`) no está incluido en el repositorio.

## 👤 Autores
- Mario Livia Auqui
- Facundo Sanchez
- Tomas Mele
- Ignacio Lucas Rodriguez
