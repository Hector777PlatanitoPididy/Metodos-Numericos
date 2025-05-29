# Métodos Explicación 

---

## 1. Interpolación Lineal

Aproxima el valor de \( y \) para \( x = 1.5 \) usando una recta entre dos puntos consecutivos del conjunto \((0, 1), (1, 3), (2, 5), (3, 7)\). Calcula la pendiente entre los puntos que encierran \( x \) y evalúa la recta. Es simple pero limitado a tramos lineales.

---

## 2. Interpolación Polinómica (Método de Lagrange)

Construye un polinomio que pasa exactamente por todos los puntos \((0, 1), (1, 3), (2, 5), (3, 7)\). Usa el método de Lagrange para calcular \( y \) en \( x = 1.5 \), combinando términos ponderados por productos de diferencias. Es preciso pero costoso para muchos puntos.

---

## 3. Método de Regresión (Lineal)

Ajusta una recta \( y = mx + b \) al conjunto de puntos \((0, 1), (1, 3), (2, 5), (3, 7)\) minimizando el error promedio. Calcula la pendiente \( m \) y el intercepto \( b \) usando fórmulas de sumas de productos. Es idéntico a Mínimos Cuadrados en este caso.

---

## 4. Método de Correlación

Calcula el coeficiente de correlación de Pearson \( r \) para medir la relación lineal entre \( x \) y \( y \) en los puntos \((0, 1), (1, 3), (2, 5), (3, 7)\). Un valor de \( r \) cercano a 1 indica una fuerte correlación lineal positiva.

---

## 5. Método de Mínimos Cuadrados (Lineal)

Ajusta una recta \( y = mx + b \) al conjunto de puntos \((0, 1), (1, 3), (2, 5), (3, 7)\) minimizando la suma de los cuadrados de los errores. Calcula \( m \) y \( b \) con fórmulas de sumas. Es idéntico a la Regresión Lineal en este contexto.
