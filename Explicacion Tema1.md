# Explicación de Errores Numéricos

---

## 🔹 1. Error de Truncamiento

**Definición:**  
Es el error que resulta al usar una **aproximación matemática** en lugar de una expresión exacta.  
Por ejemplo, en derivadas numéricas, se descartan términos de orden superior de una serie de Taylor.

**Ejemplo típico:** Diferencias finitas para calcular derivadas.

---

## 🔹 2. Error de Redondeo

**Definición:**  
Ocurre cuando un número **no se puede representar exactamente** en la memoria debido a la **precisión limitada** de los tipos de datos (como `float` o `double`).

**Ejemplo típico:** Sumar muchas veces un número muy pequeño puede acumular errores significativos.

---

## 🔹 3. Error Absoluto y Relativo

**Error Absoluto:**  
Es la **diferencia directa** entre el valor real y el valor aproximado.

**Error Relativo:**  
Es el cociente entre el **error absoluto** y el **valor real**. Permite comparar errores en magnitudes muy distintas.

---

## 🔹 4. Error de Cancelación

**Definición:**  
Sucede cuando se restan dos números muy cercanos, causando una **pérdida de cifras significativas** y, por tanto, una pérdida de precisión.

**Ejemplo típico:** Calcular `1.0000001 - 1.0000000` puede devolver un resultado impreciso.

---

## 🔹 5. Error por Criterio de Parada Inadecuado

**Definición:**  
En métodos iterativos (como Newton-Raphson), un mal criterio de parada puede llevar a:
- Parar antes de alcanzar la precisión deseada.
- Iterar de más innecesariamente.

**Ejemplo típico:** Usar solo el número de iteraciones en vez de verificar el error entre iteraciones consecutivas.

---
