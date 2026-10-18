EN PROGRESO

# Predicción de puntuación y capitalización en texto normalizado

**Materia:** Aprendizaje Automático II · Departamento de Computación, FCEN, UBA · 2026
**Tipo de trabajo:** Trabajo práctico grupal (TP II)

## 🎯 Objetivo

Dado un texto en minúsculas y sin puntuación, predecir para cada token:

- **Puntuación inicial:** `¿` o ninguna.
- **Puntuación final:** `,` `.` `?` o ninguna.
- **Capitalización:** `0` minúsculas · `1` primera en mayúscula · `2` mixta (ej. *McDonald's*) · `3` todo en mayúsculas (ej. *UBA*).

Tiene aplicación directa en el postprocesamiento de salidas de sistemas de reconocimiento automático del habla (ASR).

**Ejemplo**

```
Entrada: cuándo salimos para la uba ya se hace tarde por dónde andarán
Salida:  ¿Cuándo salimos para la UBA? Ya se hace tarde. ¿Por dónde andarán?
```

## 🧠 Modelos implementados

| Modelo | Detalle |
|---|---|
| Clásico con embeddings | Algoritmo no secuencial (ej. Random Forest) usando el promedio de embeddings de la palabra |
| Clásico sin embeddings | Mismo tipo de algoritmo con atributos artesanales (#vocales, #acentos, etc.) |
| RNN | Recurrente estándar (LSTM/GRU) |
| RNN bidireccional | Recurrente bidireccional (LSTM/GRU) |

Los tokens se generan con `bert-base-multilingual-cased`. Los embeddings son los **estáticos** del vocabulario (sin contexto); el contexto lo construyen las capas recurrentes.

## 📏 Evaluación

Las predicciones salen a nivel token, pero se evalúan a nivel **palabra** con F1 macro:

| Tarea | Clases |
|---|---|
| Puntuación inicial | `¿`, ninguna (2) |
| Puntuación final | `,` `.` `?`, ninguna (4) |
| Capitalización | 0, 1, 2, 3 (4) |


## 🧰 Tecnologías

Python · PyTorch · Hugging Face Transformers · scikit-learn · pandas

## 👤 Autores
- Mario Livia Auqui
- Facundo Sanchez
- Tomas Mele
- Ignacio Lucas Rodriguez
